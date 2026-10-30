# Administração do portfólio

## Navegação pública e indexação

A LP em `/` não divulga links para autenticação ou administração. O acesso administrativo é feito diretamente por `/login`; `/admin` sem sessão redireciona para `/login`. Sessão com refresh disponível pode passar por `/login?renew=1` para renovação, sempre dependente da identidade Neon e da autorização no banco. Login e admin têm meta robots e cabeçalho HTTP noindex/nofollow, e ficam fora do sitemap. Essas regras de busca não substituem as verificações no servidor.

Implementação: `/login`, `/admin` e API REST `/api/admin/*`. O painel possui Projetos, Mídias, Textos da LP, Guia do portfólio e Configurações. A identidade visual acompanha os formulários existentes (Segoe UI, cinzas neutros e controles de 44px).

## Conteúdo pesquisado

Pesquisa em 21/10/2026, também disponível na aba Guia do portfólio:

- Projetos selecionados, contexto, papel, processo e resultados: [Behance Project Basics](https://help.behance.net/hc/en-us/articles/204483644-Guide-Project-Basics).
- Imagens e demonstrações para apresentar o trabalho: [Behance Portfolio](https://www.behance.net/blog/how-to-make-design-portfolio).
- Vídeos e apresentações: [Adobe Portfolio](https://help.myportfolio.com/hc/en-us/articles/360036483773-Add-video-audio-and-embedded-content).
- PDFs para material completo e slides exportados, descrição alternativa para imagens, textos de apresentação, sobre, contato e metadados são decisões desta implementação.

## Segurança

Neon Auth existente continua responsável por verificar e armazenar senhas com hash, nunca criptografia reversível. O cliente chama REST; nenhuma comparação de senha ou concessão de permissão acontece no frontend. Cadastro público existente não concede acesso administrativo.

`AdminMember` autoriza por ID estável do usuário, independente de alterações de e-mail. Access token opaco de 256 bits (15 minutos) e refresh token de 384 bits (7 dias), armazenados como SHA-256 no banco. Cookies HttpOnly, SameSite=Strict, Secure em produção. Renovação troca ambos atomicamente e mantém o refresh antigo inutilizável. Cada requisição também confirma identidade no Neon; logout ou revogação do Neon bloqueiam a sessão administrativa. O refresh depende de sessão Neon válida. Não há JWT/localStorage.

Alterações de senha/e-mail são encaminhadas pelo backend ao Neon Auth. Senha exige a atual, mínimo de 12 caracteres e revogação das sessões administrativas; alteração de e-mail depende de suporte e configuração de verificação do provedor. Não alterar tabelas do Neon Auth manualmente. Fluxos de mudança precisam de teste com conta e caixa postal reais antes de produção.

Mutações exigem Origin igual ao host da requisição; usar HTTPS e proxy de confiança em produção. Respostas privadas sem cache. Login usa os controles de abuso do provedor; configurar rate limit adicional no host antes de produção.

Uploads privados em bytea no PostgreSQL (primeira versão), máximo de 8 MB, MIME e assinatura verificados. PNG, JPEG, WebP, PDF e MP4; apresentação exportada como PDF. SVG/HTML e PPTX recusados. Downloads autenticados como attachment com nosniff/sandbox. Validação de assinatura não substitui antivírus; armazenamento dedicado, cotas e inspeção ficam para evolução. Excluir projeto mantém anexos na biblioteca.

Referências: [OWASP Password Storage](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html), [OWASP Session Management](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html).

## Ativação autorizada e aplicada

Em 21/10/2026, após autorização explícita, o SQL de `prisma/admin-schema.sql` foi registrado em `prisma/migrations/20261021193000_admin/migration.sql`, testado em cópia isolada e aplicado via `prisma migrate deploy` na branch production do projeto Neon configurado. As cinco tabelas administrativas e o histórico do Prisma foram criados. O schema neon_auth permaneceu sob gestão exclusiva do provedor. `prisma migrate status` confirmou o banco atualizado.

Ambiente pretendido: banco Neon apontado por DATABASE_URL_UNPOOLED, cuja identificação precisa ser confirmada sem expor credenciais. Risco: bloqueios breves de catálogo e falha se nomes já existirem. Não há remoção de dados prevista. Antes da aplicação autorizada, criar branch/backup Neon e conferir SQL contra schema real. Recuperação: voltar à branch anterior ou remover somente as novas tabelas após exportar conteúdo, mediante autorização específica. Não executar db push/reset como atalho.

A conta indicada pelo usuário foi criada pelo comando oficial `neon neon-auth user create`, sem senha padrão, e seu ID foi autorizado com INSERT parametrizado em AdminMember. A aplicação continua concedendo permissão por ID, nunca por e-mail enviado pelo navegador.

Backup prévio confirmado: snapshot `snap-royal-math-b6ssikyu`, nome `before-admin-activation-20261021`, origem `br-patient-king-b6bfvyer`, criado às 19:27:02 UTC. O snapshot foi preservado. A branch isolada `admin-migration-check-20261021` expira em 22/10/2026 às 19:27 UTC; os testes usam contas sintéticas somente nela. Recuperação requer autorização específica e deve preservar eventuais dados criados após a ativação.

Primeiro acesso: abrir `/login`, escolher **Primeiro acesso ou esqueci minha senha**, informar o e-mail autorizado, solicitar código e definir senha de pelo menos 12 caracteres. O código e a senha são verificados no backend Neon via `/api/auth/email-otp/request-password-reset` e `/api/auth/email-otp/reset-password`. A entrega na caixa postal real depende do provedor e não foi simulada como entrega concluída. Nenhum código foi solicitado pelo agente para o e-mail real.

O contrato OpenAPI do provedor foi consultado: troca de e-mail usa `email-otp/request-email-change` e `email-otp/change-email`, com confirmação por código no novo endereço; o endpoint genérico change-email não está exposto neste ambiente. A API administrativa foi ajustada para esse contrato.

## API e evolução

- Session: GET identidade; POST cria sessão após login Neon; PATCH rotaciona tokens; DELETE encerra.
- Projects: GET lista; POST cria/edita; DELETE exclui.
- Media: GET metadados; POST multipart anexa; DELETE exclui; GET media/:id baixa.
- Content: GET textos; PUT salva campo permitido.
- Settings: POST altera e-mail/senha via provedor.

O painel persiste o catálogo e o status editorial. A página pública existente ainda é scaffold; integrar os projetos publicados, galerias e textos ao layout final da LP é a próxima etapa e está explicitado no painel. Nenhum anexo é publicado automaticamente.

Validações na branch isolada: permissão de membro, gravação/leitura/exclusão de projetos, textos, upload/download autenticado, rejeição de assinatura inválida, rotação e rejeição de refresh reutilizado, layout móvel e logout. O teste opt-in está em `tests/e2e/admin-live.spec.ts` e exige servidor em localhost:3100 conectado à mesma branch de ADMIN_TEST_DATABASE_URL, distinta da conexão de produção. A UI de primeiro acesso tem teste com API simulada para evitar envio de e-mail. Trocas reais de senha/e-mail e entrega de código ainda dependem de interação com caixa postal; a senha do administrador não foi definida nem conhecida pelo agente.

Resultado final: build, typecheck, validação de schema, status da migration e cinco testes Playwright aprovados. O teste autenticado rodou em branch isolada, com captura móvel revisada; os outros quatro cobrem acesso anônimo, origem externa e interface de login/primeiro acesso. Nenhum deploy, commit ou push foi executado nesta ativação.
