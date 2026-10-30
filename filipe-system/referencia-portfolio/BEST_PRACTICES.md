# Best practices

## Organização e código

- Ler [AGENTS.md](AGENTS.md) explicitamente em cada ferramenta; suas regras de autorização governam o fluxo de trabalho.
- Manter componentes pequenos por responsabilidade; extrair reutilização real sem construir uma biblioteca genérica antecipadamente.
- TypeScript estrito, tipos explícitos nas fronteiras e validação de conteúdo externo. Evitar `any`, casts para silenciar erros e supressões sem justificativa.
- Conteúdo público em `src/data/`; estilos globais mínimos, tokens centralizados e CSS de componente onde fizer sentido.
- Usar HTML nativo antes de recriar semântica com ARIA. Conteúdo e contato continuam acessíveis sem animação.
- Não instalar dependências para funções simples já atendidas pela plataforma. Fixar runtime compatível e um único lockfile do gerenciador escolhido; não ignorar lockfiles.

## Performance, conteúdo e SEO

Otimizar imagens com dimensões e formatos apropriados, carregamento tardio abaixo da dobra e prioridade consciente para a imagem principal. Evitar lazy loading da imagem que determina o LCP. Fontes locais licenciadas apenas se necessárias, com estratégia que preserve legibilidade. Carregar JavaScript somente para interação real.

Metas de campo: LCP ≤ 2,5 s, INP ≤ 200 ms, CLS ≤ 0,1 no percentil 75 por dispositivo. Lighthouse ajuda no diagnóstico em laboratório, mas não substitui dados de usuários nem comprova sozinho INP real. [Referência: Web Vitals](https://web.dev/articles/vitals).

Usar títulos e descrições específicos, links rastreáveis, domínio correto no canonical e texto de projetos que descreva contribuição verificável. Nunca inventar clientes, resultados, depoimentos ou disponibilidade.

## Verificação proporcional

No scaffold, criar scripts reais para checagem de tipos, lint, build e preview; só então registrar comandos de uso. Até lá, verificar documentos, links relativos e regras do ignore. Não relatar build/testes da aplicação como aprovados enquanto ela não existir.

Quando implementada a LP, validar navegação, menu móvel se houver, contato e links de projetos. Testes automatizados devem cobrir comportamento crítico; evitar testes que apenas reproduzem a implementação. Mudanças visuais pedem inspeção em navegador, teclado, responsividade, contraste e movimento reduzido. Acessibilidade automática complementa revisão manual.

## Branch e PR

Usar uma branch por tarefa e diffs pequenos e revisáveis. Implementação não concede permissão para commit/push. Após validação local e autorização, selecionar arquivos explicitamente e revisar o staged; publicar somente com autorização específica. PR descreve problema, solução, validação e limitações. Revisão precede merge; merge/deploy precisam de autorização.

O `.gitignore` filtra arquivos não rastreados; não remove arquivos do índice. Conferir com `git check-ignore` e revisar também os rastreados antes de publicação. [Documentação do Git](https://git-scm.com/docs/gitignore). Fluxo de colaboração: [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow).

## Manutenção

Atualizar roadmap e documentos junto com mudanças relevantes. Registrar decisões e alternativas na arquitetura quando houver impacto estrutural. Markdown autoral fica em `docs/`; não mover arquivos internos de skills instaladas. Nunca usar documentação desatualizada para presumir autorização de banco ou publicação.
