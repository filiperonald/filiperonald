# Security

## Atualização: painel administrativo

Ativação autorizada em 21/10/2026: snapshot preservado, migration aplicada e permissão concedida por ID. Primeiro acesso e recuperação usam OTP validado pelo Neon; nenhum segredo foi criado no frontend. E-mail administrativo novo exige confirmação por código. Entrega real de e-mail e alterações de credenciais ainda precisam da ação do titular. Veja [Admin](ADMIN.md); o aviso de schema não aplicado abaixo descreve o estado anterior.

`/api/admin/*` verifica tokens opacos, autorização no banco e identidade Neon no servidor. Access/refresh em cookies HttpOnly, refresh rotativo e hashes no banco. Alterações de senha/e-mail passam pelo provedor existente. Origem validada nas mutações; uploads privados com limites, validação de assinatura e download protegido. Veja [Admin](ADMIN.md) para decisões, testes e limitações. Schema ainda não aplicado; não considerar o painel operacional até ativação e teste real.

## Superfície do MVP

O escopo agora inclui servidor Next.js, Neon Postgres e Auth, solicitados pelo usuário. `DATABASE_URL`, `NEON_AUTH_BASE_URL` e `NEON_AUTH_COOKIE_SECRET` são lidos somente no servidor; `.env.local` e `.neon` estão ignorados. O SDK oficial faz a gestão das sessões. `/account` usa proxy de autenticação e `/api/account` verifica a sessão antes de consultar o banco, com resposta sem cache e erros sem detalhes de infraestrutura. Riscos principais: acesso indevido, vazamento de credenciais, dependências comprometidas e dados privados publicados acidentalmente. Antes de disponibilizar para usuários reais, conferir domínios confiáveis, verificação de e-mail e SMTP de produção da Neon.

## Repositório e segredos

- Aplicar o fluxo e o checklist de [AGENTS.md](AGENTS.md) em toda tarefa. Nunca commit/push sem autorização explícita.
- Manter `.env*`, chaves, credenciais, dumps, logs e dados privados fora do Git. `.env.example` só com nomes e placeholders.
- `.gitignore` não protege arquivo já rastreado nem evita que um segredo seja escrito em código. Revisar nomes e conteúdo dos arquivos, inclusive lockfiles, assets e Markdown.
- Secrets do futuro backend devem ficar no gerenciador do ambiente, com menor privilégio e rotação. Tudo servido ao navegador deve ser considerado público.
- Se houver exposição, interromper publicação, revogar/rotacionar e avaliar alcance. Remoção do histórico exige plano e autorização; não substituir rotação por exclusão de arquivo.
- Habilitar revisão obrigatória, checks e proteção contra segredos no GitHub quando disponíveis. Configurações remotas ainda não foram aplicadas.

Referências: [OWASP — Secrets Management](https://cheatsheetseries.owasp.org/cheatsheets/Secrets_Management_Cheat_Sheet.html) e [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow).

## Conteúdo e navegador

- Não renderizar HTML arbitrário sem sanitização; evitar APIs que injetem conteúdo bruto. Validar URLs de conteúdo e aceitar somente protocolos adequados, como HTTPS e `mailto:` conforme o campo.
- Publicar apenas materiais próprios ou licenciados. Revisar capturas de projetos para dados de clientes e pessoas.
- Links externos em nova aba recebem `rel="noopener noreferrer"` quando pertinente; links e ícones precisam de nomes acessíveis.
- Evitar scripts de terceiros; documentar domínio, necessidade e dados tratados quando inevitáveis.
- Configurar HTTPS, `X-Content-Type-Options: nosniff`, `Referrer-Policy` e `Permissions-Policy` adequada no host. Elaborar CSP compatível com os recursos reais, testar inicialmente em Report-Only e então aplicar; evitar liberar `unsafe-inline` indiscriminadamente.
- Avaliar HSTS após confirmar HTTPS e efeito nos subdomínios. Esses headers dependem do host e ainda não estão configurados.

## Dependências e futuras coletas

Versionar lockfile, revisar scripts de instalação e adicionar apenas pacotes necessários. Analisar vulnerabilidades por alcance e exploração; não aplicar atualização forçada que quebre o projeto sem revisão.

Caso um formulário seja aprovado: validar no servidor, limitar tamanho e frequência, proteger contra spam e impedir exposição de chaves no cliente. Definir finalidade, retenção, acesso, exclusão e informação de privacidade antes de coletar dados. Não registrar corpo de mensagens ou e-mails em logs públicos.

Migrations e qualquer alteração de schema exigem autorização específica conforme [Database](DATABASE.md).
