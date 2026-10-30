# Loading, abertura e barras de progresso

Distinguir: progresso de leitura (posição na página), progresso real (bytes/itens/etapas) e espera indeterminada. Não inventar porcentagem para uma operação não mensurável.

## Barra de leitura

Faixa discreta, transform-origin à esquerda e scaleX entre 0 e 1. CSS scroll timeline com fallback rAF/listener passivo. Fórmula: scrollY / (scrollHeight - innerHeight), protegendo distância zero. Atualizar em resize e mudança de altura. aria-hidden quando decorativa; não anunciar cada pixel.

## Espera real

Skeleton com espaço reservado ou mensagem simples. Em progresso medido, expor nome e valores acessíveis. Feedback de erro e tentativa novamente; permitir cancelamento quando aplicável. Não apagar dados sem necessidade.

## Abertura de marca

Opcional e excepcional. Não atrasar a tarefa para exibir uma animação. Se exigida, oferecer pular, evitar repetir a cada navegação e ter saída independente do sucesso de todas as imagens. Dispensar com movimento reduzido.

O portfólio tem abertura temática com espera mínima e limite temporal. Essa escolha específica não é um padrão a repetir em novos projetos.

Testar offline, rede lenta, timeout, erro, navegação durante espera e retorno à página. Nenhuma tela fica bloqueada indefinidamente.
