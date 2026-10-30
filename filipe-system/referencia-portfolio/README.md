# Portfólio — documentação do MVP

## Atualização — LP implementada

A página inicial `/` apresenta o portfólio de Filipe Ronald, com projetos, Sobre mim, exploração de disciplinas e contato pelo GitHub informado. Não há links de login/administração na LP. `/login` é o acesso restrito; `/admin` exige sessão válida. Sitemap e robots estão implementados. Conteúdo, direção visual e limites em [LP](LP.md). O estado de scaffold descrito abaixo é histórico.


Status: scaffold Next.js com build aprovado; Neon Postgres/Auth configurados na branch `production` e três testes de navegador aprovados, incluindo o fluxo real de autenticação e consulta ao banco. Hospedagem do frontend ainda não configurada.

Objetivo: uma landing page de portfólio em português que apresente o profissional, comprove sua experiência por projetos reais e facilite o contato.

## Índice

- [CI/CD, checks antes do deploy e detecção de credenciais](CI_CD.md)
- [Instruções para agentes](AGENTS.md)
- [Architecture](ARCHITECTURE.md)
- [Security](SECURITY.md)
- [Roadmap](ROADMAP.md)
- [Design system](DESIGN_SYSTEM.md)
- [Memória de identidade e decisões](memory=ai.md) — guia visual local em `/layout-guide`
- [Best practices](BEST_PRACTICES.md)
- [Database](DATABASE.md)
- [Neon: configuração e validação](NEON.md)

Todos os Markdown autorais do projeto ficam em `docs/`. Arquivos de skills preexistentes em `.agents/` e `.github/skills/` permanecem nos caminhos de instalação.

**Carregamento de instruções:** como `AGENTS.md` está em `docs/`, ferramentas que procuram esse arquivo somente nos diretórios ancestrais do código podem não carregá-lo. Configure o agente para ler `docs/AGENTS.md` ao iniciar qualquer tarefa neste repositório. Esse documento não instala hooks nem proteções no GitHub.

## Decisões iniciais

Next.js com App Router + React + TypeScript estrito + CSS nativo são a stack definida pelo usuário. Priorizar Server Components e páginas pré-renderizadas, usando Client Components para interações necessárias. Instalados: Next.js 16.4.2, React 19.3.1 e TypeScript 7.0.2, com Node 24.15.0 e pnpm 12.14.0. Não instalar CMS, ORM ou banco sem uma necessidade concreta. Contato inicial por link de e-mail e redes profissionais, sem formulário que colete dados.

Pesquisa realizada em 21/10/2026. Fontes oficiais e critérios estão nos documentos correspondentes. Para instalar dependências, executar `pnpm install --frozen-lockfile` na raiz. O `pnpm-lock.yaml` deve ser versionado; `node_modules/` está ignorado pelo Git. Scripts disponíveis: `pnpm dev`, `pnpm build`, `pnpm start`, `pnpm typecheck` e `pnpm test:e2e`. Prisma ORM 7.10.1 está configurado para PostgreSQL na Neon; `pnpm db:generate`, `pnpm db:validate` e `pnpm db:studio` estão disponíveis. Dev, tipos e build geram o Prisma Client automaticamente. O comando solicitado `npm run build` também executa o build usando as dependências instaladas por pnpm; não criar um segundo lockfile. Lint ainda não configurado.
