# Memória do projeto

## Arquivo atualizado de Sobre mim — 21/10/2026

Durante a troca da hero, o usuário também anexou `f0d1e6b2-21ef-42c1-8c61-12bb98357e1a.jpg` para substituir o retrato de Sobre mim. O arquivo fornecido foi incluído em `public/images/filipe-ronald-profile.jpg`, mantendo o enquadramento quadrado e as bordas do design system. Um novo caminho de asset evita reutilização do cache do retrato anterior.

## Substituição da imagem da hero — 21/10/2026

O usuário rejeitou a paisagem anterior e forneceu `A260155_large.jpg`, foto horizontal de automobilismo, para a hero. A versão de publicação está em `public/images/hero-motorsport.jpg`, com 2400px de largura e sem metadados EXIF. A imagem mantém proporções com cover, posição central a 65% no desktop e 60% horizontal no celular, preservando o carro no recorte. A camada verde de contraste e o conteúdo da hero permanecem. A paisagem anterior deixa de ser usada.

## Foto de fundo na abertura — 21/10/2026

O usuário forneceu uma foto própria em https://i.imgur.com/JUdkXfl.jpeg e pediu aplicá-la ao fundo da seção inicial. Original vertical de 960 × 1280px, sem EXIF, preservado em `public/images/hero-landscape.jpeg`. A LP usa Next Image com preload, preenchimento cover e posição central a 52%, preservando proporções por recorte responsivo. Uma camada de verde profundo com opacidade 0,68 preserva o branding e a leitura do texto claro. A imagem é decorativa, não recebe descrição duplicada e não intercepta links ou foco.

## Foto na seção Sobre mim — 21/10/2026

O usuário forneceu sua foto em https://i.imgur.com/HqTf7tx.jpeg e solicitou incluí-la em Sobre mim. A imagem foi preservada em `public/images/filipe-ronald.jpeg` (640 × 640px, sem EXIF), servida localmente pelo Next Image, com dimensões explícitas, texto alternativo e bordas do design system. A composição mantém a imagem completa e equilibra o texto ao lado no desktop; no celular, os elementos ficam em uma coluna. Commit e push seguem a autorização já concedida na conversa.

## Refinamento e publicação autorizados — 21/10/2026

O usuário pediu aprimorar o layout com Impeccable e as orientações de Emil Kowalski, mantendo o branding. Em seguida, solicitou aplicar o fr. do cabeçalho ao ícone do navegador e autorizou commits por etapas com push para main. A LP e o favicon foram publicados no commit 1525cbe. O refinamento preserva cores, Manrope e conteúdo; ajusta ritmo, tablet/celular, estabilidade do seletor e feedback. Detalhes em [POLISH.md](POLISH.md). A autorização desta tarefa não concede permissão para migrations.

## LP implementada — 21/10/2026

A pedido do usuário, foi aplicada a skill Taste para construir a rota pública `/`, seguindo o briefing mais recente. Direção sorteada: The name as a monument, seed 72207545. Manrope local, paleta verde, nome em grande escala e seções claras para projetos. O site atual é o único trabalho apresentado, sem clientes, métricas ou outros projetos inventados. Textos de apresentação e Sobre mim são propostas editoriais para revisão. Contato usa apenas GitHub já informado.

Nova instrução do usuário: não mostrar acesso/login na página principal; login em `/login`, proteção de `/admin` e redirecionamento anônimo. “No index” foi interpretado como noindex para login/admin; sitemap lista somente a página principal. Sem commit, push, migration ou deploy. Ver [LP](LP.md).


## Atualização do briefing — respostas de 21/10/2026

Estas respostas posteriores prevalecem sobre registros anteriores conflitantes. São decisões de briefing; o guia e os tokens ainda não foram atualizados.

- Nome público confirmado: **Filipe Ronald**.
- Escopo informado agora: portfólio de **marketing, branding e UI/UX**, sem prioridade entre áreas. Front-end deixa de ser presumido como área de destaque.
- Não foi indicado público comercial prioritário; o usuário esclareceu que a intenção é ser um portfólio.
- Abertura escura e projetos em fundo claro.
- Títulos com tipografia geométrica com personalidade, combinados com fontes neutras e legíveis em textos longos. O usuário citou serif e Montserrat como referências; família e combinação finais ainda não escolhidas. Montserrat é uma família sem serifa.
- Componentes arredondados e animações mais expressivas, incluindo animação de scroll. Implementação deverá respeitar movimento reduzido e manter conteúdo acessível.
- Associação profissional desejada: design e branding. Nenhuma contribuição ou evidência específica foi fornecida nesta resposta.
- Ações desejadas: explorar projetos e acessar a seção interna **“Sobre mim”**, destino confirmado pelo usuário em 21/10/2026.
- Personalidade confirmada pelo usuário em 21/10/2026: **sóbrio e preciso + criativo e experimental**, alternativa A. A ambiguidade anterior está resolvida.
- Verde principal e restrição ao amarelo permanecem definidos; hexadecimais, raios, fontes e parâmetros de movimento ainda são escolhas a propor.

## Finalidade

Registrar o que for definido para a identidade visual e o design system do portfólio. Este arquivo contém contexto, decisões e pendências; não concede autorização para operações externas.

## Solicitação — 21/10/2026

- Criar Markdown de design system e rota `/layout-guide`.
- Partir da estrutura fornecida: branding, design system, design da LP, conteúdo/microcopy e documentação/implementação.
- Perguntar os dados que faltam antes de consolidar a identidade.
- Registrar e organizar as definições neste arquivo, chamado literalmente `memory=ai.md`, em `docs/` conforme a organização do repositório.

## Definido pelo usuário

- Conteúdo inicial: projetos do GitHub pessoal `filiperonald`, informado na resposta 8 em 21/10/2026: https://github.com/filiperonald.
- Conteúdo futuro: links de imagens, vídeos, apresentações PowerPoint, planilhas e marcas criadas pelo usuário. Os links serão fornecidos posteriormente; não bloquear a definição visual pela ausência desses materiais.

- Marca pessoal, conforme resposta 5 em 21/10/2026. O nome exato ainda não foi confirmado; Filipe Ronald é o nome existente no projeto.
- Objetivo prioritário: construir autoridade, conforme resposta 6 em 21/10/2026.
- Preferências de cor: verde como preferência principal; não gosta muito de amarelo; gosta razoavelmente de azul. Resposta 7 em 21/10/2026. Tratar azul como possibilidade secundária, sem obrigar sua inclusão; evitar amarelo na proposta visual.
- Referência fornecida: https://cnpjotas-webinars-hazel.vercel.app/ — referência para o uso de verde, sem autorização para copiar sua identidade integralmente.

- Linguagem visual: tech, conforme resposta 3 em 21/10/2026. Cores, fontes e tratamentos específicos ainda não definidos.
- Base visual: mista, conforme resposta 4 em 21/10/2026, combinando áreas claras e escuras. Distribuição entre seções ainda pendente.

- Produto: landing page de portfólio com identidade visual consistente.
- Áreas de atuação: UI/UX, front-end e branding, conforme resposta 1 em 21/10/2026. Não foi definida uma prioridade entre elas.
- Público: combinação de públicos, conforme resposta 2 em 21/10/2026. A composição exata e a prioridade entre recrutadores, clientes e agências ainda não foram especificadas.
- Proporção visual: referência global de 60% dominante/base, 30% secundária/estrutura e 10% acento/destaque, sem obrigação matemática em cada seção.
- Documentar regras de cores, tipografia, grid, espaçamento, formas, ícones, bordas, sombras, componentes, estados, responsividade e acessibilidade.
- Desenvolver futuramente toda a copy alinhada ao posicionamento; nenhuma copy final foi aprovada nesta etapa.

## Contexto encontrado — não equivale a aprovação da marca

- O scaffold usa o nome Filipe Ronald; confirmar grafia de apresentação. O posicionamento como marca pessoal foi confirmado depois.
- Stack existente: Next.js App Router, React, TypeScript e CSS nativo.
- Já havia proposta de base neutra clara, acento azul e tipografia de sistema em `DESIGN_SYSTEM.md`.
- A aplicação atual contém autenticação e conta; não foi solicitada substituição dessas telas.

## Implementado nesta etapa

- Documento principal: [DESIGN_SYSTEM.md](DESIGN_SYSTEM.md).
- Rota pública `/layout-guide`: marca, proporção de cores, tokens, tipografia, layout, componentes, estrutura de conteúdo e perguntas pendentes.
- Tokens provisórios centralizados em `src/styles/tokens.css`; CSS Modules no guia, sem novas dependências.
- Navegação global inclui acesso ao guia.
- Proposta existente preservada como provisória: base `#fafaf9`, texto `#18181b`, acento `#1d4ed8`, fonte Segoe UI/Arial/sans-serif.
- O guia usa exemplos documentais, sem projetos, contatos ou provas profissionais inventadas.

## Perguntas enviadas — aguardando resposta

| Tema | Pergunta | Resposta |
| --- | --- | --- |
| Área | UI/UX, front-end, branding, multidisciplinar ou outra? | UI/UX, front-end e branding. Respondido em 21/10/2026; sem prioridade definida. |
| Público | Recrutadores, clientes, agências ou combinação? Prioridade? | Combinação. Respondido em 21/10/2026; composição e prioridade a detalhar. |
| Linguagem | Editorial, minimalista, experimental, tech ou orgânica? | Tech. Respondido em 21/10/2026. |
| Base | Clara, escura, mista ou explorar? | Mista, com áreas claras e escuras. Respondido em 21/10/2026. |
| Marca | Pessoal ou estúdio? Nome exato? | Pessoal. Respondido em 21/10/2026. Nome exato a confirmar. |
| Objetivo | Emprego, freelance ou autoridade? Prioridade? | Autoridade. Respondido em 21/10/2026. |
| Referências | Sites, cores preferidas e estilos a evitar? | Referência Cnpjotas Webinars; preferência principal por verde, evitar amarelo, azul com afinidade moderada. Respondido em 21/10/2026. |
| Evidências e contato | Projetos, contribuições, diferenciais e links publicáveis? | Projetos do GitHub pessoal filiperonald; depois, links de imagens, vídeos, PowerPoints, planilhas e marcas próprias. Respondido em 21/10/2026. Curadoria, contribuições e contatos adicionais ainda pendentes. |

## Conteúdo e formatos do portfólio

- Fonte inicial: [GitHub filiperonald](https://github.com/filiperonald).
- Consulta à API pública do GitHub em 21/10/2026 retornou apenas o repositório público `filiperonald`, sem descrição: https://github.com/filiperonald/filiperonald. A consulta não permite concluir se existem projetos privados ou em outras fontes.
- Não promover automaticamente todo repositório a estudo de caso. Verificar contexto, contribuição, material visual, demonstração e resultados disponíveis.
- Formatos previstos: repositório/site, imagem, vídeo, apresentação, planilha e identidade de marca.
- Cada trabalho deverá ter título, categoria, resumo, papel/contribuição e links opcionais com rótulos específicos, como “Ver código”, “Assistir ao vídeo”, “Ver apresentação” e “Abrir planilha”.
- Imagens precisam de texto alternativo; vídeos, de legendas ou alternativa textual; apresentações e planilhas, de resumo legível na página. Downloads devem informar formato e tamanho quando conhecido. Prévia somente com material real.
- Os formatos e a fonte foram documentados; integração automática com GitHub, upload e incorporação de serviços externos não foram implementados nesta etapa.

## Validação da implementação inicial

- Build direto (`node node_modules/next/dist/bin/next build`): aprovado, `/layout-guide` pré-renderizada.
- Scripts `pnpm typecheck` e `pnpm build`: inicialmente impedidos por `prisma generate`, adicionado por trabalho simultâneo no workspace, com CLI indisponível naquele momento. Typecheck direto também encontrou imports Prisma ainda não resolvidos. Não alterar essa integração como parte do guia.
- Inspeção no navegador em 1440, 768 e 390 px: sem falhas automáticas de layout/contraste; avisos de título grande, seções abaixo da dobra e respiro nas amostras de cores são aceitáveis para um guia de referência longo, sem função de dashboard.
- Teclado: skip link, âncora de ação e abertura de details com Enter aprovados. Sem overflow da página em 320, 375, 390, 768, 1024 e 1440 px. Conteúdo visível com preferência de movimento reduzido.
- Tabela permite rolagem local por teclado em telas estreitas para preservar tokens e hexadecimais legíveis.
- Revalidação final: teclado, responsividade e inspeção passaram após ajuste da tabela. O typecheck geral segue falhando por arquivos de administração/Prisma adicionados simultaneamente (`src/app/admin`, `src/app/api/admin` e `src/lib/admin.ts`), fora do escopo desta tarefa. O build aprovado acima corresponde ao estado anterior a essas alterações simultâneas.
- Sem script de lint configurado. Não executar migrations, commit, push ou deploy nesta etapa.

## Próxima consolidação da identidade

### Leitura da referência e proposta de direção — 21/10/2026

- Referência acessada no navegador, HTTP 200; screenshot local de inspeção em `test-results/branding-reference.png` (artefato ignorado).
- Cores observadas por estilos computados: verde profundo `#173f35`, verde mais escuro `#0f332c`, fundos claros `#f6f8f2` e verde claro `#e1ebe4`. O amarelo/âmbar observado `#f6b339` não deve orientar a proposta, conforme preferência do usuário.
- Estes valores descrevem a referência, não constituem paleta aprovada nem tokens adotados. O extrator web não conseguiu abrir a página; a inspeção foi feita diretamente com Playwright.
- Proposta a desenvolver: base mista com neutros claros e campos de verde profundo; verde como assinatura, sem amarelo decorativo. Azul opcional apenas se houver função clara.
- Para o objetivo de autoridade, priorizar estudos de caso que expliquem raciocínio, decisões e contribuições em UI/UX, front-end e branding. Essa organização é proposta, dependente do material real.
- Acento azul e base clara atuais no guia permanecem como demonstração técnica anterior, não representam a direção final solicitada.

Registrar cada resposta com data e origem na conversa. Atualizar a especificação e o guia juntos. Definir proposta de valor, personalidade, tom e conceito; depois fechar cores e tipografia, estruturar as seções e escrever títulos, textos e CTAs finais. Identificar propostas como propostas até confirmação.
