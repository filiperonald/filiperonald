# Acessibilidade e mobile

HTML semântico, landmarks e títulos hierárquicos. Links/botões com nomes claros, foco visível e ordem previsível. Modal com foco gerenciado, retorno ao acionador e saída por Escape quando apropriada.

Contraste AA: texto normal 4,5:1; texto grande 3:1 (18 pt normal ou 14 pt em negrito). Elementos necessários de controles e indicadores: 3:1 conforme o critério aplicável. Conferir estados e texto sobre fotos. Não comunicar erro só por cor.

Alvos: pelo menos 24 × 24 CSS px ou condições/exceções de espaçamento do critério WCAG 2.2; projetar perto de 44 × 44 px facilita o toque. Labels persistentes e erros associados aos campos; placeholder não substitui label.

No mobile, considerar safe-area, teclado virtual e dvh/svh conforme o layout. Fonte de inputs pelo menos 16 px quando necessário para evitar zoom indesejado. Não bloquear pinch zoom. Hover só em dispositivos compatíveis; gestos sem disputa de eixos.

Inspecionar desde 320 px, larguras intermediárias e desktop. Zoom 200%, texto ampliado, orientação horizontal, nomes longos e mensagens extensas não podem impedir tarefas. Pontos de inspeção não são breakpoints obrigatórios.

Testar teclado, movimento reduzido e, quando viável, leitor de tela/dispositivo real. Se apenas emulou, declarar isso. Auditoria automatizada não substitui revisão manual.

Fontes: [W3C contraste](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html), [alvos](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html), [C39](https://www.w3.org/WAI/WCAG22/Techniques/css/C39.html).
