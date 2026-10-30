# Design system

Defina personalidade, público, promessa e ação principal antes da paleta. Tecnologia pode aparecer na precisão da composição; não exige neon ou efeitos em tudo. Evite aplicar a mesma hero e os mesmos cards a qualquer segmento.

## Tokens

Antes de consolidar a direção, aplique [ANTI-AI-SLOP.md](ANTI-AI-SLOP.md): composição, conteúdo e detalhes precisam responder à marca e à tarefa, com revisão do resultado renderizado.

Use papéis semânticos: fundo, superfície, texto, secundário, ação, texto sobre ação, borda, foco, sucesso, aviso e erro. Defina modos claro/escuro e confira contraste por estado.

Referência opcional do portfólio:

| Papel | Valor |
| --- | --- |
| Fundo escuro | #102e25 |
| Texto no escuro | #eff3e9 |
| Base clara | #f3f5ef |
| Texto | #153b30 |
| Acento | #b9e582 |
| Superfície | #e3e9dd |
| Fonte | Manrope variável local |

Não aplicar automaticamente esta identidade a outras marcas. Snapshot completo: ../referencia-portfolio/tokens.css.

## Escalas iniciais

- Espaço: 4, 8, 12, 16, 24, 32, 48, 64 e 96 px, conforme conteúdo.
- Corpo: 16–18 px; entrelinha 1,5–1,7; largura de leitura perto de 60–70 caracteres.
- Títulos fluidos com limites; tracking ajustado à família, sem prejudicar leitura.
- Gutter: começar perto de 20 px no celular e ampliar conforme viewport.
- Raios por função e sombras para camadas reais. Não arredondar tudo sem critério.
- 60/30/10 como heurística de composição, não obrigação ou substituto de contraste.

## Componentes e aceitação

Documentar anatomia, variantes e estados: normal, hover, foco, ativo, desabilitado, loading e erro. Links navegam; botões executam ações. Ícones de uma família, com nomes acessíveis quando interativos.

Conferir teclado, texto longo, zoom e mobile. Não duplicar tokens arbitrariamente; registrar exceções. A identidade deve acomodar conteúdo real antes de ser considerada consolidada.
