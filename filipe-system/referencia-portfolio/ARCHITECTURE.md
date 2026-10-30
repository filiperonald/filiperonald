# Architecture

## Estado atual — LP pública

A rota `/` é a LP pré-renderizada do portfólio. Conteúdo tipado em `src/data/portfolio.ts`, CSS Module próprio e tokens centralizados. A fonte Manrope é local, com licença OFL. Somente navegação dependente de rota, exploração de disciplinas e observação de entradas usam Client Components. A LP não consulta o banco nem publica anexos privados. O catálogo administrativo continua aguardando integração editorial explícita. `/admin` verifica sessão no servidor; acesso anônimo redireciona para `/login`. Sitemap contém somente `/`; rotas restritas têm noindex. Detalhes em [LP](LP.md).


## Atualização: administração

Ativação em 21/10/2026: banco migrado e acesso administrativo concedido à conta escolhida, após backup e teste isolado. Primeiro acesso por código de e-mail em `/login`, sem senha padrão. Consulte [Admin](ADMIN.md) para o estado atual; a pendência de aplicação descrita abaixo é histórica.

O escopo solicitado agora inclui `/login`, `/admin`, CRUD de projetos, biblioteca privada de mídia, textos editáveis e configurações de acesso. Neon Auth mantém identidade e senhas; tabelas próprias controlam autorização administrativa e access/refresh tokens opacos. Implementação, pesquisa e limites em [Admin](ADMIN.md). Schema e SQL preparados; ativação no banco aguarda autorização específica. A integração do catálogo ao layout público continua pendente.

## Contexto e decisão proposta

A LP precisa apresentar identidade, projetos e contato com boa leitura em celular e carregamento rápido. A stack definida pelo usuário é **Next.js com App Router, React, TypeScript em modo estrito e CSS nativo**. Priorizar páginas pré-renderizadas e Server Components; usar Client Components apenas para interações que exijam execução no navegador. A escolha substitui a proposta inicial de Astro. [Documentação oficial](https://nextjs.org/docs/app).

Estado atual: scaffold Next.js implementado, build de produção aprovado e Neon Postgres/Auth configurados e testados no projeto solicitado; ver [Neon](NEON.md). Next.js 16.4.2, React 19.3.1 e TypeScript 7.0.2 estão registrados em `package.json`; Node 24.15.0 em `.node-version` e pnpm 12.14.0 no campo `packageManager`. Usar pnpm e versionar `pnpm-lock.yaml`.

## Estrutura planejada

```text
/
├── docs/                  # Toda documentação Markdown autoral e AGENTS.md
├── public/                # Arquivos publicados sem proteção; favicon, robots
├── src/
│   ├── assets/            # Imagens e fontes processadas no build
│   ├── components/        # Elementos reutilizáveis
│   ├── sections/          # Hero, projetos, sobre e contato
│   ├── app/               # layout.tsx, page.tsx, not-found.tsx e metadados
│   ├── data/              # Conteúdo público tipado: perfil, projetos, links
│   └── styles/            # Tokens, base e estilos globais mínimos
├── tests/                 # Testes de fluxos críticos quando implementados
├── .gitignore
├── next.config.ts        # A criar no scaffold
├── tsconfig.json          # A criar no scaffold
└── package.json           # A criar; scripts só após existirem
```

O scaffold atual contém `src/app/`, `src/components/` e `src/lib/`; as demais pastas da árvore são planejamento. `neon.ts` declara Auth. As pastas `.agents/` e `.github/` contêm ferramentas locais e precisam de revisão antes de publicação.

## Fluxo e limites

Conteúdo público tipado → Server Components do Next.js → páginas pré-renderizadas → hospedagem com HTTPS/CDN → navegador. CSS cuida do layout; Client Components atendem interações reais. Nenhum segredo participa do HTML ou bundle público.

O conteúdo permanece separado do layout. Cada projeto tem slug único, título, resumo, papel, tecnologias, imagem/alt e links opcionais validados. Sem links inventados ou cards clicáveis sem destino. Componentes recebem dados por propriedades, sem dependência de banco.

Contato inicial: `mailto:` e links profissionais; depende de cliente de e-mail ou serviço externo do visitante. Formulário com entrega garantida é uma feature posterior e exigirá endpoint, proteção contra abuso e política de dados.

## Build e entrega

- Definir scripts de desenvolvimento, tipos, lint, build e preview no scaffold.
- PR: instalar pelo lockfile, conferir tipos/lint/build e fluxos críticos. A configuração de CI ainda está pendente.
- Selecionar hospedagem compatível com Next.js, HTTPS, headers e previews; não contratar nem publicar nesta etapa. Avaliar exportação estática conforme recursos e hospedagem: pré-renderização não implica exportação estática.
- Configurar domínio real, canonical, sitemap e robots na implantação; impedir indexação de previews conforme recursos do host.
- Build aprovado não autoriza deploy. Se a hospedagem publicar automaticamente ao fazer push/merge, considerar esse efeito antes de pedir a autorização correspondente.

## Fora do MVP

Dashboard de negócio, CMS, blog, múltiplos idiomas e analytics. Postgres, Auth e a API autenticada de conta foram incluídos por solicitação explícita. Mudanças de escopo precisam atualizar este documento, o roadmap e a política de segurança.
