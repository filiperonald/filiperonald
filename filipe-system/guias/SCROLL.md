# Scroll e revelação

Revelar blocos com IntersectionObserver, perto da área visível. HTML começa visível; habilitar estado de entrada somente após inicializar a melhoria visual. Um erro de JS não deve esconder a página.

Ponto de partida: 16 px verticais, opacity, 550 ms; stagger de 50–80 ms em poucos elementos relacionados. Revelar uma vez por padrão. Não adiar título, CTA e informação necessária à tarefa.

Preservar scroll nativo. Evitar captura de roda/toque e smooth scroll artificial sem necessidade demonstrada. Âncoras sob header fixo usam scroll-margin-top. Sticky precisa caber na viewport e funcionar em zoom/mobile.

Para movimento contínuo, avaliar CSS scroll timelines com detecção de suporte. No fallback JS, listener passivo e um rAF pendente no máximo. Recalcular com mudanças de altura. Progresso limitado a 0–1, com proteção para distância zero.

Paralaxe leve só com propósito, sem corpo de leitura em movimento. Desativar movimentos decorativos com preferência reduzida. Testar âncora direta, voltar/avançar, imagens tardias, resize, teclado, scroll rápido e ausência de JS.
