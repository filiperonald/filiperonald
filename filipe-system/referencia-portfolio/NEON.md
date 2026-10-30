# Neon — Postgres e Auth

## Escopo e configuração

Solicitação do usuário: provisionar Postgres e Auth na organização `org-soft-mud-87768171`, projeto `super-cherry-83958446`, branch `production`. O CLI global instalado é `neon` 8.10.1. O MCP do Codex foi configurado globalmente com OAuth em `https://mcp.neon.tech/mcp`, sem chave de API no repositório; sua autenticação no cliente ainda precisa ocorrer no primeiro uso. Skills `neon`, `neon-postgres` e `neon-auth` estão em `.agents/skills/`.

O comando `neon init` criou `.neon` e `neon.ts`, inicialmente em modo offline. O login humano foi concluído no navegador aberto por `neon deploy`; o CLI verificou o projeto e aplicou a configuração à branch `production` (`br-patient-king-b6bfvyer`). O projeto é AWS São Paulo (`aws-sa-east-1`), sem restrição de IP nem bloqueio de conexões públicas; nenhuma dessas proteções foi removida.

O deploy informou `No changes — branch production already matches the policy`, `Utilized services: Postgres, Neon Auth` e `Pulled 5 Neon variables into .env.local`. Os serviços já existiam e foram reutilizados. `neon neon-auth status` confirmou `better_auth` na base `neondb`.

```powershell
neon login
neon deploy
```

O deploy aplica a declaração de Auth e busca as variáveis do projeto em `.env.local` (ou `.env`, se já existir). O aplicativo não publica seu frontend com esse comando. Não criar outro projeto nem uma branch substituta para contornar falha de acesso.

## Integração

- `src/lib/db.ts`: pool `pg`, exclusivo do servidor Node; `attachDatabasePool` quando executado na Vercel. `src/lib/prisma.ts` reutiliza esse pool via `@prisma/adapter-pg`, e a API usa o Prisma ORM. A hospedagem ainda não foi escolhida. Edge sem suporte TCP exigiria reavaliar o driver.
- `src/lib/auth/server.ts`: SDK `@neondatabase/auth/next/server`, inicialização sob demanda com URL real e segredo de cookies.
- `src/app/api/auth/[...path]/route.ts`: proxy oficial dos métodos de autenticação.
- `src/proxy.ts`: restringe `/account`, mantendo formulários, assets e API de Auth acessíveis.
- `/api/account`: verifica a sessão no servidor, depois executa `SELECT true AS connected, $1::text AS user_id`; não modifica tabelas e não aceita SQL do cliente.
- `/auth/sign-up`, `/auth/sign-in` e `/account`: cadastro, entrada, restauração da sessão, consulta autenticada e saída. Erros e estados de carregamento são apresentados ao usuário.

Variáveis privadas: `DATABASE_URL`, `NEON_AUTH_BASE_URL`, `NEON_AUTH_COOKIE_SECRET`. O segredo de cookie foi gerado localmente por fonte criptográfica; valores não são registrados nesta documentação. `.env.example` contém somente placeholders. `.env.local`, `.neon` e `node_modules/` estão ignorados. Não desativar validação TLS no driver.

Não há migration de negócio. O schema e as tabelas de Auth são gerenciados pela Neon ao provisionar o serviço solicitado. A implantação do frontend e mudanças em schema de negócio continuam fora desta etapa.

## Validação executada

`pnpm install --frozen-lockfile`, `npm run typecheck` e `npm run build` passaram. O app iniciou com `npm start -- --hostname 127.0.0.1` e respondeu em `http://127.0.0.1:3000`.

Após o deploy e o reinício do servidor, `pnpm test:e2e`: **3 passaram em 4,2 segundos**, usando Edge real. Foram verificados formulário em celular sem overflow, resposta 401 da API sem sessão, redirecionamento da página protegida, cadastro real, consulta Postgres autenticada com o mesmo ID da sessão, restauração após recarga, saída, rejeição de senha incorreta e nova entrada. Os testes não usam mocks de Auth ou banco.

Saída final resumida:

```text
npm run build
✓ Compiled successfully in 1039ms
Finished TypeScript in 1144ms
✓ Generating static pages using 9 workers (6/6)

npm start -- --hostname 127.0.0.1
✓ Ready in 403ms

pnpm test:e2e
3 passed (4.2s)
```

Para repetir as verificações, com as variáveis locais presentes:

```powershell
npm run build
npm start -- --hostname 127.0.0.1
# Em outro terminal:
pnpm test:e2e
```

Os testes usam Edge instalado e criam um usuário sintético `@example.com` no Auth da branch vinculada. Não armazenam senha, trace, vídeo nem screenshot do fluxo autenticado. O usuário de teste permanece no Auth; não há exclusão automática. Se verificação obrigatória de e-mail impedir a sessão, será necessário um inbox de teste real para completar esse fluxo, preservando as configurações de segurança.

A revisão visual Taste em 1440, 768 e 390 px retornou zero falhas e dois avisos sobre espaço livre da tela de login. Direção Achromatic ledger, seed 2016500964, com CSS nativo, fonte do sistema e fundo azul-cinza. Formulários simples mantêm o espaço livre; não foram adicionados dados ou ilustrações de preenchimento.

## Problemas encontrados

- No PowerShell, `--services postgres,auth` foi convertido em um único valor inválido com espaço; usar `--services 'postgres,auth'` resolveu.
- pnpm bloqueou o postinstall de `core-js` transitivo. O script foi inspecionado e explicitamente desabilitado em `pnpm-workspace.yaml`; a instalação reproduzível passou depois disso.
- O SDK atual de Auth é `0.6.0-beta` e traz dependências transitivas depreciadas e avisos de peers em Better Auth/better-call e TypeScript. O build e a checagem de tipos passaram; não foram forçadas versões transitivas incompatíveis para silenciar os avisos.
- A primeira rodada não tinha variáveis remotas: um teste passou e dois pararam nas precondições. Após login/deploy, o teste real revelou um redirecionamento de login prefetched antes da sessão. A navegação após entrar/sair agora usa um novo documento para descartar o cache de rotas anterior à mudança de autenticação. A rodada final passou integralmente.

Pendências de publicação: autenticar o MCP no primeiro uso, escolher hospedagem e domínio do frontend, configurar domínio confiável e SMTP de produção conforme o uso real. Os testes criaram contas sintéticas no Auth de `production`, incluindo contas de diagnóstico; elas permanecem lá. Nenhum usuário real foi alterado ou removido.

Referências: [skill oficial](https://neon.com/.well-known/agent-skills/neon/SKILL.md), [Auth para Next.js](https://neon.com/docs/auth/quick-start/nextjs-api-only), [escolha do driver](https://neon.com/docs/connect/choose-connection).
