# Animações e microinterações

Anime para orientar, confirmar, explicar continuidade ou expressar a marca em momentos pontuais. Em tarefas repetidas, prefira feedback rápido e estável.

| Uso | Ponto de partida |
| --- | --- |
| Controle | 120–180 ms |
| Menu/popover | 160–240 ms |
| Entrada editorial | 450–650 ms, 12–24 px |
| Hero expressiva | Até 800 ms, pontual |

Curvas iniciais: cubic-bezier(.16,1,.3,1) para entrada/saída suave; cubic-bezier(.23,1,.32,1) para feedback curto. Springs para gestos e continuidade física; preservar velocidade ao interromper. Os números são propostas, não regras universais.

Preferir transform/opacity. Medir filtros, blur e máscaras. CSS para estados simples, WAAPI ou biblioteca existente para sequências; rAF quando atualização por quadro for necessária. Evitar re-render por frame, leituras/escritas intercaladas e will-change global.

Com prefers-reduced-motion, remover deslocamentos/paralaxe e entregar estado final. Não depender de animationend para liberar ação ou conteúdo. Limpar frames, timers e listeners ao desmontar. Testar interrupções, repetição, navegação e aba em segundo plano.

Fonte: [W3C — C39](https://www.w3.org/WAI/WCAG22/Techniques/css/C39.html). Consultar também as skills originais animate, animation-performance e review-animations.
