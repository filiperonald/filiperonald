# Vercel — instalação e build

Atualização da LP: `SITE_URL` pode ser configurada com o domínio público definitivo, sem credenciais. Sitemap e robots usam esse domínio; sem a variável, usam a origem da requisição. A página principal é pré-renderizada e indexável; login, admin e rotas de apoio têm noindex e não entram no sitemap. O build continua sem aplicar migrations. Veja [LP](LP.md).

## Causa do erro NEXT_NO_VERSION

O log fornecido mostra a implantação de `main` no commit `482e2e0`. Esse commit contém somente `README.md`, sem `package.json`, Next.js, lockfile ou código da aplicação. A aplicação atual ainda está em arquivos locais não rastreados. Repetir a implantação do mesmo commit não inclui esses arquivos.

O `package.json` local declara Next.js em `dependencies`. A correção remota depende de versionar os arquivos da aplicação, publicar uma branch e integrar a alteração à branch usada pela Vercel. Commit, push e merge continuam sujeitos às autorizações do projeto; esta tarefa prepara a configuração local.

## Configuração versionada

`vercel.json` define o framework Next.js, instala pelo lockfile usando pnpm 12.14.0 explicitamente e executa `npm run vercel-build`. O script chama `npm run build`, que gera o Prisma Client antes de executar `next build`. O comando explícito evita depender da versão global de pnpm da imagem de build. `node_modules/`, `.next/`, `.env.local`, `.neon` e o client Prisma gerado permanecem fora do Git.

No painel Vercel, conferir:

- Root Directory: raiz do repositório, onde ficam `package.json`, `pnpm-lock.yaml` e `vercel.json`; não usar `src/` ou `docs/`.
- Node.js: 24.x, conforme `engines.node`.
- Output Directory: padrão do framework Next.js.
- Production Branch: integrar a correção à branch configurada antes de executar novo deploy de produção.
- Variáveis privadas do runtime: `DATABASE_URL`, `NEON_AUTH_BASE_URL`, `NEON_AUTH_COOKIE_SECRET`. `DATABASE_URL_UNPOOLED` é usada pelo CLI Prisma para futuras operações autorizadas; não aplicar migrations durante o build.

O build não consulta o banco: pode gerar o client sem URL de banco. As variáveis reais são necessárias para Auth e consultas quando o aplicativo estiver rodando. Configure-as no painel Vercel para os ambientes usados, sem publicar arquivos `.env`.

Além do deploy do frontend, registrar o domínio real no Neon Auth e manter o mesmo segredo de cookies entre instâncias do mesmo ambiente. Não adicionar credenciais a `vercel.json`.

Referências: [configuração da Vercel](https://vercel.com/docs/project-configuration/vercel-json) e [Root Directory](https://vercel.com/docs/builds/configure-a-build).

## Verificação local e entrega

Validado em cópia isolada, sem `.env.local`, `node_modules` ou Prisma Client previamente gerado. A instalação com o comando de `vercel.json` passou usando o lockfile. `npm run vercel-build` gerou o client, compilou o Next.js, aprovou TypeScript e gerou 13 páginas estáticas. Esta é uma verificação local Windows; o build remoto Linux ainda depende da publicação dos arquivos e de novo deploy na Vercel.

Branch local: `fix/vercel-next-build`. Título proposto para PR: `Fix Vercel Next.js detection and Prisma build`. Descrição: publicar a aplicação Next.js que ainda estava somente local e configurar instalação reprodutível com pnpm 12.14.0; gerar Prisma Client antes do build. Validação: instalação pelo lockfile e build em cópia limpa sem segredos. Não incluir `.env.local`, `.neon`, `node_modules` ou artefatos gerados. Commit, push e PR remoto ainda não executados.
