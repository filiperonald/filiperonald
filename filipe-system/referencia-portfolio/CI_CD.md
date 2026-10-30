# CI/CD antes do deploy

Pesquisa e implementação em 21/10/2026. Este documento separa checks executáveis agora, evoluções recomendadas e configuração externa ainda pendente.

## Pipeline implementado

Workflow: `.github/workflows/ci.yml`. Executa em todo PR, push para `main`, acionamento manual e semanalmente às segundas, 08:20 UTC. Não usa credenciais de produção, não aplica migrations e não publica o frontend.

| Check | Verificação | Critério de falha |
| --- | --- | --- |
| Secrets and detector tests | Gitleaks CLI 8.30.1; histórico completo disponível no checkout e arquivos atuais; política de arquivos privados rastreados; testes do detector | Credencial detectada, arquivo privado versionado, erro do scanner ou teste falhando |
| Types, schema, build and E2E | Instalação pelo lockfile, Prisma validate, TypeScript, build Next, scan de `.next/static` e `public/`, nove testes Playwright | Qualquer comando falha |
| Dependency audit | `pnpm audit --audit-level high`, incluindo desenvolvimento e produção | Advisory high/critical ou falha de consulta ao registry |
| Ready for deploy | Agrega todos os jobs com `if: always()` | Qualquer job falha, é cancelado ou pulado |

Node segue `.node-version` (24.15.0); pnpm segue `packageManager` (12.14.0). Actions externas estão fixadas por SHA completo; Dependabot propõe atualizações semanais de Actions e pacotes npm/pnpm. Cache contém o store do pnpm, não `.env` ou saída do servidor. Nenhum job recebe secrets. Permissões são `contents: read`, checkout sem credenciais persistidas e execução em `pull_request`, nunca código de PR com `pull_request_target`. São práticas alinhadas ao [guia de segurança do GitHub Actions](https://docs.github.com/en/actions/reference/security/secure-use).

O lint ainda não está instalado no projeto. Não foi criado um comando fictício nem apresentado TypeScript como substituto de lint. A próxima evolução deve adicionar ESLint flat config, `eslint-config-next/core-web-vitals` e regras TypeScript, corrigir a base e só então exigir `pnpm lint`. O guia da versão instalada em `node_modules/next/dist/docs/01-app/03-api-reference/05-config/03-eslint.md` orienta usar ESLint CLI.

## Credenciais: cobertura e testes

A action local `.github/actions/setup-gitleaks/action.yml` baixa o CLI de release fixa e verifica SHA-256 antes de executar. O CLI é usado diretamente, sem depender do licenciamento da action comercial para organizações. Configuração em `.gitleaks.toml`: regras padrão do provedor mais regras próprias para URLs PostgreSQL/MySQL com senha e `NEON_AUTH_COOKIE_SECRET`. Referências: [Gitleaks CLI e configuração](https://github.com/gitleaks/gitleaks) e [condições da Gitleaks Action](https://github.com/gitleaks/gitleaks-action).

O checkout usa `fetch-depth: 0`; `gitleaks git --log-opts="--all"` verifica o histórico das refs disponíveis, incluindo credenciais removidas em commits seguintes. Isso não cobre forks, refs remotas não baixadas, logs de outros serviços ou arquivos privados fora do checkout. `gitleaks dir` verifica os arquivos atuais. Diretórios de dependências e Prisma gerado estão excluídos; documentos, código, workflows e arquivos de exemplo continuam cobertos. O build público é escaneado separadamente, incluindo os bundles JavaScript e CSS. Arquivos binários, imagens e texto dentro de fotografias não recebem OCR: revisar assets manualmente continua necessário.

`scripts/test-secret-scanner.mjs` cria fixtures aleatórias em diretório temporário, sem armazenar tokens no repositório, e verifica:

1. Exemplos vazios e os placeholders exatos existentes passam.
2. URL de banco com senha é bloqueada.
3. Cookie secret atribuído é bloqueado.
4. Token de provedor reconhecido pelas regras padrão é bloqueado.
5. Credenciais reais em `.env.example` continuam bloqueadas.
6. Remover o token deixa a árvore limpa, mas o scan do histórico continua bloqueando.
7. Ferramenta ausente ou erro de execução não é aceito como detecção bem-sucedida: somente o exit code específico 23 vale como positivo.

Logs usam `--redact=100`; não são enviados relatórios contendo segredos como artifacts. Exceções existentes exigem simultaneamente caminho `.env.example` e valor exato do placeholder. Não excluir o arquivo inteiro, não aceitar baseline automática de todos os achados e não usar `continue-on-error` para aprovar vazamentos. Se houver segredo real, interromper a publicação e revogar/rotacionar; a exclusão do arquivo não desfaz a exposição.

Complemento recomendado: ativar [Secret Scanning e Push Protection](https://docs.github.com/en/code-security/secret-scanning/introduction/about-push-protection) quando disponíveis no plano. Actions executa depois do push: bloqueia aprovação pelo gate, mas não impede a chegada inicial de um segredo ao GitHub. Um hook local do scanner ajuda antes do push, sem substituir o controle remoto.

## Testes de aplicação e banco

`playwright.ci.config.ts` tem allowlist dos arquivos `portfolio.spec.ts` e `admin.spec.ts`, Chromium instalado explicitamente, um worker, prazo máximo e servidor de produção local na porta 3100. Não lê `.env.local` e remove variáveis de banco/Auth do ambiente do servidor. Os testes existentes cobrem navegação, teclado, responsividade de 320 a 1440px, movimento reduzido, estabilidade do seletor, SEO, admin anônimo, origem externa e recuperação de senha com API simulada. A configuração de desenvolvimento com Edge permanece disponível. [Playwright em CI](https://playwright.dev/docs/ci) e [browsers](https://playwright.dev/docs/browsers).

Não executar `pnpm test:e2e` indiscriminadamente no CI: `neon.spec.ts` contém cadastro real e exige Neon; `admin-live.spec.ts` grava projetos, textos, mídias e permissões. Recomenda-se um workflow separado de integração, em ambiente confiável e banco/Auth isolados, com limpeza de contas e dados, segredos restritos ao ambiente e nenhuma execução em PR externo. Antes disso, adaptar o teste administrativo: o INSERT atual fornece somente `userId`, enquanto o schema normalizado exige `AdminMember.id` UUID gerado pelo cliente; SQL bruto não recebe automaticamente o default Prisma. Revisar também limpeza de `SiteContent`, usuários e permissão após falhas. Migrations, inclusive em banco efêmero, continuam exigindo autorização específica; não adicionar `migrate deploy` ao build ou ao CI por conveniência.

Testes unitários recomendados quando essas rotinas forem extraídas: validação de assinatura/tamanho de uploads, expiração/rotação de sessão e validação de campos. Os E2E sem banco não comprovam persistência nem login real. Não há entrega de OTP real simulada como concluída.

## Segurança adicional e prioridade

| Prioridade | Controle | Situação |
| --- | --- | --- |
| Obrigatória agora | Segredos com testes, tipos, schema, build, E2E, audit e gate agregado | Implementado |
| Próxima | ESLint e análise estática de segurança JS/TS | Configurar antes de considerar a cobertura completa |
| Próxima | Revisão de alterações do lockfile no PR | Dependabot implementado; dependency-review-action depende de elegibilidade do repositório |
| Próxima | Integração real com Neon isolado | Depende de adaptação dos testes e ambiente autorizado |
| Complementar | Acessibilidade automatizada e Lighthouse CI com orçamento estável | Não substituem teclado, leitor de tela ou métricas de campo |
| Complementar | Verificar YAML e segurança dos workflows com actionlint/zizmor em CI | Recomendado ao evoluir o pipeline |

CodeQL e dependency-review-action não foram habilitados às cegas: o repositório consultado é privado e pertence a uma conta pessoal. [CodeQL](https://docs.github.com/en/code-security/concepts/code-scanning/codeql/codeql-code-scanning) e [Dependency Review](https://github.com/actions/dependency-review-action) possuem requisitos de disponibilidade para repositórios privados. Avaliar elegibilidade/licença ou alternativa de análise estática antes de adicioná-los como checks obrigatórios. A [auditoria pnpm](https://pnpm.io/cli/audit) implementada verifica advisories conhecidos, não vulnerabilidades inéditas no código da aplicação.

## Como impedir deploy antes dos checks

O job `Ready for deploy` é um resultado de CI, não um bloqueio técnico da Vercel. No estado consultado, a API de proteção de `main` retornou HTTP 403 pedindo GitHub Pro ou repositório público; portanto não afirmar que merge/push estejam protegidos. Nenhum plano, ruleset ou configuração do host foi alterado nesta tarefa.

Há duas estratégias:

1. **Manter integração Git da Vercel:** quando disponível, exigir os checks antes de integrar a `main`. Isso reduz risco, mas pushes diretos e reexecuções exigem cuidado. Para impedir atribuição de domínio de produção antes da aprovação, configurar [Vercel Deployment Checks](https://vercel.com/docs/deployment-checks), conforme disponibilidade. Essa estratégia pode construir um deployment antes dos checks; não equivale a impedir toda criação de deployment.
2. **Exigir CI antes de qualquer deploy:** mover publicação para job dependente de `Ready for deploy` no mesmo workflow e desativar os deployments automáticos concorrentes da integração Git. Usar ambiente GitHub `production` e credenciais Vercel somente nesse job, após checks do mesmo SHA. O fluxo oficial é `vercel pull`, `vercel build` e `vercel deploy --prebuilt`; é preciso configurar projeto, organização, token e política de produção antes de ativar. [GitHub Actions com Vercel](https://vercel.com/kb/guide/how-can-i-use-github-actions-with-vercel).

A segunda estratégia atende literalmente “rodar antes de subir para deploy”. O workflow entregue prepara os checks, mas não introduz publicação automática nem solicita/expõe tokens. Evitar dois canais de deploy ativos, `workflow_run` que baixa código de PR com credenciais, e promoção de artifact de SHA diferente do validado. Um smoke test após deploy deve consultar LP, login, robots e sitemap sem gravar dados; ele complementa, não substitui, o gate anterior.

## Validação desta entrega

Local Windows: typecheck, Prisma validate, build, nove testes Chromium usando a configuração CI, teste de detecção de segredos e audit high/critical aprovados. Histórico Git disponível: 16 commits analisados sem segredos encontrados após revisar seis ocorrências de placeholders exatos. Scan de `.next/static` sem achados; `public/` contém imagens binárias, sem conteúdo textual analisável pelo scanner. Essas verificações não provam ausência absoluta de credenciais. Execução Linux e resultados remotos devem ser conferidos no GitHub Actions após publicar.
