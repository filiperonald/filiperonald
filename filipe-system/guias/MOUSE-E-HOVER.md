# Mouse e hover

Efeitos de mouse são melhorias opcionais: ativar com `(hover: hover) and (pointer: fine)` e sem movimento reduzido. Conferir pointerType em dispositivos híbridos. Toque não pode ficar preso em hover.

- Ações: cor/borda e feedback até 180 ms; foco visível equivalente.
- Foto: zoom discreto, como 1.02–1.04, em recorte estável.
- Magnetismo: deslocamento limitado, por exemplo até 6 px; manter a área clicável fácil de alcançar.
- Tipografia reativa: assinatura ou hero; texto acessível inteiro e spans decorativos sem leitura duplicada.
- Cursor personalizado: excepcional; preservar o cursor nativo e a compreensão das ações.

Separar leituras de geometria e escritas de estilo. Evitar getBoundingClientRect por letra a cada frame; cache invalidado em mudanças de layout quando viável. Usar refs para estilos dinâmicos, sem render React contínuo.

Retornar ao repouso em pointerleave. Ao mudar preferência ou desmontar, limpar efeito, listeners e frames. Limitar passo de tempo após aba inativa. Nenhum loop permanece ativo em repouso.

Aceite: teclado acessa o mesmo conteúdo; touch funciona sem hover; efeito não cria overflow nem dificulta o clique.
