# Refinamento da LP — Impeccable e Emil Kowalski

## Projeto de fotografia Inhotim — 26/10/2026

Incluído Inhotim no catálogo público, na categoria Fotografia, ao lado de Retratos Falados. O card segue a apresentação tipográfica existente; os detalhes exibem a capa real da série e o link para [o projeto completo no Behance](https://www.behance.net/gallery/190321023/Inhotim).

A capa foi obtida na listagem pública do [perfil de Filipe Ronald](https://www.behance.net/filipe), que associa a imagem ao projeto 190321023. Arquivo local: `public/images/inhotim-cover.jpg`, 808 × 632px, sem metadados EXIF. A página individual recusou consulta automática; os textos descrevem apenas o projeto informado pelo titular e elementos visíveis na capa, sem inferir outras fotografias ou resultados.

Validação: typecheck, build e lint Taste aprovados. Capturas da categoria e dos detalhes revisadas em 390, 768 e 1440px, com a imagem carregada e sem overflow horizontal. O inspector Taste não iniciou o Chrome neste ambiente; a inspeção foi feita com Playwright/Edge. A suíte sem banco aprovou 18 testes inicialmente; o teste de cards exigiu reiniciar explicitamente o filtro Todos entre larguras, pois a navegação para a mesma URL preserva o estado do componente. Após esse ajuste, a reexecução do teste passou, completando a validação dos 19 casos. A verificação de Inhotim cobre também filtro, destino Behance e carregamento da foto em 320, 390, 768 e 1440px. Revisão local dos três arquivos de texto alterados por padrões de credenciais sem achados; Gitleaks indisponível localmente.

## Acesso direto às imagens — 23/10/2026

Removidos links de ampliação que abriam arquivos locais em outra guia, inclusive na galeria de projetos, na foto da premiação e nas capturas do seletor. A interação de inclinação/sombra permanece nos retratos. O menu de contexto e o arrasto nativo são cancelados sobre imagens para evitar salvamentos casuais; como os arquivos são necessários para exibição no navegador, isso não impede extração por ferramentas do navegador nem capturas de tela.

## Animação da foto da premiação — 23/10/2026

A foto do Dia D Cnpjotas reutiliza o mesmo componente de inclinação e sombra do retrato, preservando suas proporções e largura. O link para ampliar permanece clicável e acessível por teclado; a legenda fica estática. As mesmas restrições de mouse, hover e movimento reduzido se aplicam.

## Recomendação de Arthur Chagas — 23/10/2026

A recomendação recebida no LinkedIn foi transcrita integralmente da captura fornecida pelo titular, com atribuição a Arthur Chagas, data de 20/08/2025 e contexto de cliente. Ela aparece após a premiação e antes do contato, como blockquote em HTML, legível sem depender da captura. O original está em `public/images/recomendacao-arthur-chagas.jpeg`, acessível por link, junto do perfil LinkedIn já informado. As afirmações sobre liderança, atuação e resultados permanecem atribuídas ao autor da recomendação.

Retrato de Arthur fornecido pelo titular em `public/images/arthur-chagas.png`, exibido junto à autoria. Commit e push para main autorizados ao concluir as alterações desta sessão.

Validação conjunta: typecheck, build e 16 testes Playwright Chromium aprovados, incluindo inclinação, sombra, retorno ao repouso e mudança para movimento reduzido. Novas seções inspecionadas em 320, 768 e 1440px; avatar e retrato estático por toque emulados sem overflow. Capturas locais em `.taste-skill/`. Detector Impeccable sem achados. Revisão local por padrões de segredos limitada aos textos alterados/novos sem achados; imagens revisadas visualmente. Nenhuma migration ou dependência adicionada.

## Reconhecimento no Dia D Cnpjotas — 23/10/2026

Seção entre Sobre mim e contato apresenta o 1º lugar na categoria “Transformar Clientes em Fãs”, recebido no Dia D Cnpjotas 2024. Foto fornecida pelo titular em `public/images/dia-d-cnpjotas-2024.jpg`, exibida inteira, com texto alternativo, legenda e acesso à imagem original. A copy usa o relato do titular sobre experiências genuínas, relacionamentos duradouros e cultura de encantamento. Layout em duas colunas no desktop e uma no celular, com os tokens e entradas por scroll existentes.

## Posicionamento de Marketing — 23/10/2026

Conforme esclarecimento do titular, Marketing apresenta sua atuação estratégica na Cnpjotas: planejamento de marketing e construção de planos de ação, conectando objetivos, prioridades e execução. Título, descrição e legenda foram atualizados. A captura do site institucional permanece como prévia; os perfis e trabalhos de redes sociais estão na aba Social Media.

## Retrato com resposta ao mouse — 23/10/2026

A foto de Sobre mim acompanha o cursor com inclinação de até 5 graus por eixo e elevação de 4px. Uma sombra suave aparece abaixo e acompanha a direção oposta. A mola usa stiffness 100 e damping 10, preservando a velocidade ao mudar de direção e retornando ao repouso quando o mouse sai. O quadro de interação permanece imóvel, separado da entrada por scroll.

O efeito exige mouse, ponteiro preciso, hover e movimento permitido. Toque e movimento reduzido mantêm o retrato estático; alterações da preferência, perda de foco e cancelamento do ponteiro limpam a animação. Apenas transform e opacity são animados, com sombra pré-definida, sem dependência nova nem renderização React por frame.

## Social Media e Video Maker — 23/10/2026

O seletor de Sobre mim apresenta Marketing, Social Media, Video Maker, Branding e UI/UX, nessa ordem. Social Media reúne os perfis de Cnpjotas, Conecta Cnpjotas e Karine Campos informados pelo titular. Video Maker apresenta os dois reels fornecidos, com links diretos para assistir no Instagram. Branding continua selecionado inicialmente.

As novas prévias usam tipografia e links na identidade existente, sem imagens ou descrições de cenas inferidas. O Instagram bloqueou a consulta automática dos materiais; os destinos foram preservados conforme enviados. Não há reprodução automática nem scripts de incorporação de terceiros. A LP continua independente do catálogo administrativo.

Validação: typecheck, build e 15 testes Playwright aprovados. Após ajuste da largura do quadro, as prévias foram conferidas em 320, 390, 768 e 1440px, sem recorte dos textos ou links; capturas em `.taste-skill/social-video-*`. Detector Impeccable sem achados. Commit e push para main autorizados pelo usuário nesta sessão.

## Progresso de leitura — 22/10/2026

A LP tem uma linha fixa de 3px no topo, preenchida em verde-claro conforme a rolagem até o fim da página. O navegador usa uma scroll timeline nativa quando disponível; o fallback usa listener passivo, requestAnimationFrame e ResizeObserver, sem renderizações React por frame. O progresso acompanha mudanças na altura do conteúdo e não intercepta cliques nem altera o layout. Movimento reduzido mantém a indicação funcional, sem suavização, mola ou movimento adicional. O indicador é decorativo para leitores de tela, sem anúncios contínuos.

## Revisão mobile e iPad — 22/10/2026

Inspeção com toque emulado em 320×740, 390×844, 768×1024, 820×1180, 1024×768 e 1180×820: sem overflow horizontal nos títulos, links e controles. Filtros, abertura de detalhes e seleção de Marketing conferidos em todas essas dimensões. Em telas de até 400px, o cabeçalho foi reorganizado em duas linhas para evitar quebra de Sobre mim, mantendo a ordem do DOM. Hover do botão de tema e dos botões globais agora depende de ponteiro preciso com hover, para evitar estados presos após toque.

Capturas em `.taste-skill/mobile-audit/`. A indicação de leitura foi conferida em 0%, 50%, 100% e no retorno ao topo, incluindo movimento reduzido e fallback sem scroll timeline. Revisão em Edge/Chromium no Windows; Safari/iPadOS e aparelhos físicos não foram testados. A instalação de WebKit foi tentada, mas o download falhou por conexão/DNS. Emulação não comprova safe areas, barras do Safari ou comportamento físico de toque.

Validação final: typecheck, build e onze testes Playwright aprovados. Publicação em main autorizada pelo usuário para as alterações validadas desta sessão.

## Marketing com captura do site — 22/10/2026

A aba Marketing em Sobre mim volta a apresentar a captura local do site da Cnpjotas, usando o mesmo quadro das outras disciplinas e o link Ampliar. As prévias e os links de Instagram foram retirados dessa área. O texto mantém as informações sobre criação de peças e gestão dos perfis da Cnpjotas e do Conecta Cnpjotas; o site permanece como link de visita. A navegação entre Marketing, Branding e UI/UX foi preservada.

Verificação: typecheck, build e dez testes Playwright aprovados. Inspeção em 1440, 768 e 390px sem overflow, com capturas locais em `.taste-skill/marketing-restored/`; detector Impeccable sem achados. Commit e push para main autorizados nesta etapa.

## Capas tipográficas dos projetos — 22/10/2026

A pedido do usuário, esta versão substitui as capas com imagem e degradê por fundo verde sólido e título em destaque. Cada título termina com o ponto verde-claro da assinatura fr., com o mesmo peso 800. O formato do projeto acompanha a descrição abaixo. Todas as imagens, incluindo a antiga capa e projetos com uma única imagem, ficam disponíveis em Ver detalhes, com legenda e link para ampliar. Os testes da LP foram ajustados para verificar a ausência de imagens nos cards e sua presença nos detalhes.

Verificação: typecheck, build e dez testes Playwright aprovados; capturas em desktop, tablet e celular em `.taste-skill/cards-solid/`; detector Impeccable sem achados. Commit e push para main solicitados pelo usuário nesta etapa.

## Organização das capas dos projetos — 22/10/2026

Os seis cards passam a usar um quadro de capa consistente, com título e formato sobre um degradê verde de contraste. Capturas de interface são exibidas inteiras com margens; logos preservam suas proporções e uma área de respiro; a fotografia usa recorte central. A capa fica mais alta no celular para acomodar imagem e título. Descrições e ações permanecem alinhadas; o acesso aos detalhes recebe tratamento secundário, preservando o destaque do link de visita. Filtros, galerias complementares e navegação por teclado foram preservados.

Verificação: typecheck, build e dez testes Playwright da LP aprovados; inspeção visual em desktop, tablet e celular com capturas em `.taste-skill/cards-after/`; detector Impeccable sem achados. O inspector da página ainda aponta a abertura de carregamento preexistente sobre o título, além de avisos de título, ausência de vídeo e respiro fora da seção alterada. Nenhuma dependência ou alteração de banco.

Refinamento solicitado pelo usuário em 21/10/2026, preservando a identidade implementada no design system. Escopo: toda a LP pública e suas interações; as verificações de acesso e indexação permanecem em vigor.

## Autoridade e método

Foram aplicadas as skills locais `impeccable` e `emil-design-eng`. O comando de contexto de Impeccable identificou uma implementação visual existente, sem PRODUCT.md ou DESIGN.md separados. A orientação `SCOPED_EXISTING_ALLOWED` permite refinar esse sistema sem substituir a identidade. O conteúdo em `docs/DESIGN_SYSTEM.md`, os tokens, a implementação e as capturas anteriores foram usados como autoridade.

Não houve mudança de direção visual ou inclusão de alegações profissionais. Verde profundo, superfícies claras, acento verde-claro, Manrope local, assinatura fr., imagens existentes e nome monumental foram preservados. A avaliação independente de layout foi feita por um agente somente de leitura, conforme orientação da skill; a implementação e as verificações ficaram no agente principal.

## Revisão e resultado

| Before | After | Why |
| --- | --- | --- |
| Projeto apertado e desalinhado em 768px | Prévia acima da descrição a partir de 960px | Preserva o protagonismo da imagem e a leitura |
| Metadados e ação misturados no celular | Metadados agrupados e ação em linha própria | Torna a navegação identificável |
| Altura variável entre disciplinas | Painéis na mesma célula de grid, com inativos fora da acessibilidade | Evita saltos sem fixar alturas de texto |
| Prévia recortada ao selecionar Marketing | Quadro estável com imagem inteira em contain | Preserva as proporções do material |
| Miniaturas sem acesso ao arquivo maior | Links Ampliar nos detalhes e na prévia ativa | Permite ler o material em resolução original |
| Regras de espaçamento sobrepostas | Tokens semânticos para seção, bloco e grupo | Mantém um ritmo responsivo consistente |
| Tracking apertado e feedback de hover com deslocamento | Tracking de títulos até -0,04em, feedback de cor e pressão discreta | Melhora leitura e reduz movimento frequente |
| Troca de estado com movimento potencial por teclado | Troca imediata por teclado; transição de imagem de 180ms apenas por ponteiro | Aplica o critério de frequência e propósito de Emil |

## Implementação e limites

Os painéis de descrição inativos usam `visibility: hidden` e `aria-hidden`, mas continuam contribuindo para a medida do grid. O estado ativo permanece no mesmo lugar e o status informa a disciplina selecionada. As imagens usam um quadro de proporção estável, preenchido sem recortar o conteúdo. A troca por ponteiro usa transições CSS interrompíveis; a preferência de movimento reduzido elimina deslocamentos e transições.

Entradas editoriais usam 650ms e o nome usa 800ms. Controles usam o token de feedback de 160ms, com curva forte de saída. Não há biblioteca de animação, evento por frame ou animação de dimensões de texto. A assinatura fr. mantém o tracking próprio da marca; o nome em grande escala permanece uma decisão do branding, acima do limite genérico da skill.

O favicon solicitado usa o próprio fr. do cabeçalho: PNG e ICO gerados a partir da renderização da Manrope, com fundo #102e25, letras #eff3e9 e ponto #b9e582. O Next.js declara ambos; HTTP 200 e tipos de mídia foram conferidos.

Os quatro materiais visuais continuam sendo capturas públicas do próprio projeto. O conteúdo profissional, os contatos e o catálogo privado não foram ampliados ou publicados por inferência. Fotos, vídeos e outros cases ainda dependem de material real do titular.

## Verificação

- Nove testes Playwright aprovados, incluindo os quatro testes administrativos de leitura/mocks, navegação pública, teclado, movimento reduzido, seis larguras entre 320 e 1440px, sitemap e robots.
- Teste de estabilidade nos três estados do seletor em 390, 768 e 1024px: variação máxima aceita de 1px na altura da seção, sem regressão observada.
- Typecheck e build de produção aprovados.
- Detector Impeccable executado uma vez nos alvos alterados, como solicitado pelo contexto: resultado `[]`, sem achados.
- Inspeção visual em 1440, 768 e 390px, com capturas locais em `.taste-skill/polish-final/`; resultados do inspector: zero falhas e o aviso já conhecido de ausência de vídeo real.
- Avaliação independente confirmou resolução dos cinco achados de layout sem identificar regressões nas capturas e no código.

Os testes usam Edge no Windows. Não foi realizado teste físico em aparelho nem auditoria com leitor de tela; automação e inspeção de semântica não equivalem a essas verificações. A ausência de PRODUCT.md separado pode ser resolvida posteriormente pelo fluxo `impeccable init`, sem bloquear este refinamento.

## Entrega autorizada

O usuário solicitou commits por etapas e push para `main`. O primeiro marco, `1525cbe`, publicou a LP, as regras de acesso/SEO e o favicon, após incorporar o commit remoto de normalização das entidades. Nenhuma migration foi aplicada nesta tarefa. O refinamento é entregue em um segundo commit validado; o hash fica no histórico do Git.
