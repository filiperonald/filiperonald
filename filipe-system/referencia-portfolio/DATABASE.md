# Database

## Migração de normalização de identificadores — preparada, não aplicada

`20261021194500_normalize_entity_ids` evolui o modelo sem apagar registros existentes. Ela adiciona UUID próprio a `AdminMember` e `SiteContent`, preserva `AdminMember.userId` e `SiteContent.key` como chaves únicas de negócio, e muda `AdminSession` para referenciar `AdminMember.id` por foreign key. Sessões existentes são preenchidas a partir do vínculo atual antes da troca da constraint; a coluna redundante é removida somente depois desse preenchimento.

Projetos, mídias e novas sessões passam a gerar UUIDs na aplicação. Os IDs textuais já existentes continuam válidos e imutáveis para preservar referências e cookies já emitidos. Os índices adicionados seguem as consultas reais: sessões por membro, projetos publicados por posição e mídias por projeto/data.

O arquivo foi validado contra o schema efetivo de production por diff somente leitura. Ele ainda não foi executado em nenhum banco. Antes da aplicação, criar uma branch Neon a partir de production, aplicar usando `DATABASE_URL_UNPOOLED`, validar login, rotação de sessão, CRUD administrativo e integridade das foreign keys; depois criar snapshot e obter autorização específica para production. A migration é forward-only: após novas escritas, rollback seguro exige restauração de backup/branch porque a coluna redundante de sessão deixa de existir.

## Atualização: entidades administrativas propostas

**Estado em 21/10/2026:** migration `20261021193000_admin` aplicada com autorização explícita, após snapshot e validação em branch isolada. As cinco tabelas existem em production e `prisma migrate status` confirma histórico atualizado. A conta escolhida foi autorizada por ID em AdminMember. Detalhes e recuperação em [Admin](ADMIN.md); referências anteriores a schema não aplicado abaixo são histórico da preparação.

O schema agora define AdminMember, AdminSession, PortfolioProject, PortfolioMedia e SiteContent. O SQL revisável em `prisma/admin-schema.sql` cria somente essas entidades. Uma consulta somente leitura em 21/10/2026 confirmou banco `neondb`, schema `public`, sem essas tabelas. Nenhum DDL foi aplicado. Plano de ativação, backup e recuperação: [Admin](ADMIN.md).

## Decisão atual: Neon Postgres e Auth

O usuário solicitou explicitamente Neon Postgres e Auth no projeto `super-cherry-83958446`, organização `org-soft-mud-87768171`, branch `production`. Isso substitui a decisão inicial de não usar banco nem login. Configuração e verificação operacional: [Neon](NEON.md).

O aplicativo usa Prisma ORM 7.10.1 com `@prisma/adapter-pg` e o pool `pg` existente no servidor Node. O runtime usa `DATABASE_URL` e mantém a integração de pool para Vercel. O CLI Prisma usa `DATABASE_URL_UNPOOLED`, carregada de `.env.local` ou `.env` sem substituir variáveis injetadas. Auth continua no SDK gerenciado oficial. A consulta de verificação é somente leitura e parametrizada com `$queryRaw`; não foi criado schema de negócio nem executada migration própria. O provisionamento de Auth gerencia seu próprio schema. Conteúdo público do portfólio pode continuar local, separado dos dados de autenticação.

## Prisma ORM

- `prisma/schema.prisma`: provider PostgreSQL, sem modelos fictícios nem tabelas de Auth sob gestão do ORM.
- `prisma.config.ts`: configuração do CLI e conexão direta para futuras operações autorizadas.
- `src/lib/prisma.ts`: client singleton exclusivo do servidor, reutilizando o pool existente.
- `pnpm db:generate`: gera o client em `src/generated/prisma/`, ignorado pelo Git; também executado antes de dev, tipos e build.
- `pnpm db:validate`: valida o schema sem modificar o banco.
- `pnpm db:studio`: abre a interface administrativa. Alterações feitas no Studio modificam dados reais da branch configurada.

O PostgreSQL já está hospedado na Neon; não foi instalado servidor PostgreSQL local. Nenhum `migrate`, `db push` ou DDL foi executado. Modelos e migrations de negócio serão definidos conforme as entidades reais da aplicação. Referência: [Prisma com PostgreSQL](https://www.prisma.io/docs/orm/v7/core-concepts/supported-databases/postgresql).

Validação da instalação: `pnpm install --frozen-lockfile`, `pnpm db:validate`, `npm run typecheck` e `npm run build` passaram. Uma consulta real somente leitura pelo Prisma retornou `SELECT 1` com sucesso na Neon. Os scripts de instalação de `prisma` e `@prisma/engines` foram revisados e permitidos explicitamente em `pnpm-workspace.yaml`. A tag `prisma@latest` apontava para Prisma 8 RC; foi usada a versão estável 7.10.1 para os três pacotes Prisma.

## Contrato de conteúdo proposto

| Entidade | Campos | Validação |
| --- | --- | --- |
| Profile | nome, especialidade, resumo, contato público | Obrigatórios sem espaços vazios; só dados autorizados para publicação |
| Project | slug, título, resumo, papel, tecnologias, imagem, alt | Slug único; textos reais; imagem válida; alt segundo propósito |
| Project links | demo e repositório opcionais | HTTPS válido; omitir se indisponível |
| SocialLink | rótulo e URL | Nome acessível e protocolo permitido |

Validar contratos no build quando implementados. Não colocar tokens ou dados privados em arquivos de conteúdo, pois eles alimentam o site público. SQL de futuras migrations deve ser versionado; dumps e bancos locais devem permanecer ignorados.

## Evolução condicional

Se persistência for aprovada, avaliar PostgreSQL gerenciado ou a solução exigida pelo CMS escolhido a partir de volume, custo, região, backup e operação. Não há fornecedor escolhido nem modelo relacional aprovado. Separar desenvolvimento, preview e produção; nunca usar produção como ambiente de testes.

Antes de coletar contatos, especificar finalidade, campos mínimos, retenção, exclusão, responsáveis, acesso e informação de privacidade. Definir constraints, índices por consultas reais, credenciais de menor privilégio e conexões somente no servidor. Testes usam dados sintéticos sem dados pessoais reais.

## Regra de migrations

**Nunca aplicar migration sem autorização explícita do usuário para o ambiente e a alteração.** Inclui local, testes, staging e produção; `db push`, sync automático, DDL manual e reset também contam. CI, build e startup não podem aplicar migrations implicitamente.

Fluxo futuro:

1. Preparar schema/SQL e revisar sem executar alterações no banco.
2. Identificar ambiente, impacto em dados, locks e tempo esperado; definir backup e recuperação, considerando que reversão de schema pode não recuperar dados.
3. Apresentar plano e obter autorização específica.
4. Aplicar somente no ambiente autorizado, registrar versão/resultado e verificar integridade sem expor dados ou credenciais.

Credenciais seguem [Security](SECURITY.md) e as orientações de [OWASP Secrets Management](https://cheatsheetseries.owasp.org/cheatsheets/Secrets_Management_Cheat_Sheet.html). Não há migration pendente, banco configurado ou alteração de dados realizada nesta preparação.
