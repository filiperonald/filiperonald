# Evitar AI slop

## Objetivo

Neste guia, AI slop é trabalho genérico, superficial ou pouco revisado que parece pronto, mas não responde ao contexto real. Esta é uma definição operacional do kit. A aparência de uma página não comprova se houve uso de IA. Avaliar qualidade, coerência, utilidade e autenticidade; não tentar enganar detectores ou esconder a origem de conteúdo.

As regras abaixo são uma síntese editorial para novos projetos, informada pelas fontes ao final. Não são uma lista científica de sinais de autoria por IA.

## Antes de desenhar

1. Identifique público, tarefa principal, oferta, restrições e materiais reais no briefing. Registre lacunas; não preencha fatos ausentes com invenções.
2. Pesquise referências variadas conforme [PESQUISA-WEB.md](PESQUISA-WEB.md). Anote o princípio aproveitável e o que não copiar de cada referência.
3. Registre em [DECISOES.md](../templates/DECISOES.md) uma direção concreta: hierarquia, composição, tipografia, cor, imagens e comportamento. Explique a relação dessas escolhas com a marca e a tarefa. “Moderno”, “premium” e “clean” sozinhos não definem uma direção.
4. Organize o conteúdo e a ação principal antes de escolher efeitos ou distribuir cards. Preserve o design system existente quando houver; qualquer ruptura precisa de motivo ligado ao projeto.

## Sinais para revisar e como corrigir

| Sinal | Correção esperada |
| --- | --- |
| A mesma hero centralizada, selo, título gigante, dois botões e grade de três benefícios em qualquer projeto | Escolher a abertura pelo que o visitante precisa ver: produto em uso, trabalho, catálogo, informação ou ação. Manter essa estrutura apenas se servir ao conteúdo. |
| Toda informação vira card, com o mesmo peso e espaçamento | Criar hierarquia por importância. Usar listas, tabelas, texto, imagens ou agrupamentos simples conforme a relação entre os dados. |
| Gradiente, brilho, vidro, ruído, blobs, emojis ou ícones usados para preencher espaço | Remover o que não comunica, orienta ou pertence à identidade. Não substituir automaticamente por outra tendência. |
| Tipografia e paleta escolhidas por padrão da ferramenta | Conferir compatibilidade com marca, idioma, legibilidade e conteúdo. Uma fonte comum pode ser a escolha certa; não buscar exotismo por obrigação. |
| Todas as seções têm a mesma composição e extensão | Ajustar ritmo e densidade ao assunto, preservando consistência. Não forçar assimetria em tarefas que exigem leitura rápida. |
| Dashboard com gráficos decorativos, números arbitrários ou controles sem efeito | Mostrar dados com origem, unidades e período; conectar controles a comportamento real. Identificar demonstrações e estados indisponíveis. |
| Movimento constante, entrada de cada linha ou scroll que atrasa o acesso | Animar para comunicar estado, continuidade ou resposta. Garantir leitura imediata, controle e movimento reduzido. |

Nenhum desses recursos é proibido isoladamente. Cor roxa, Inter, cards, simetria ou gradientes não são evidência de baixa qualidade. O problema é a escolha automática, repetitiva e sem justificativa. Em ferramentas e documentação, padrões familiares ajudam o usuário; a personalidade deve respeitar essa função.

## Texto com conteúdo

- Escrever o que o produto faz, para quem e em quais condições. Trocar “Transforme sua experiência com uma solução inovadora” por uma descrição verificável da tarefa.
- Usar títulos que informam e CTAs que antecipam a ação. Exemplo de rótulo: “Exportar PDF” no lugar de “Desbloquear possibilidades”, quando a ação realmente exporta PDF.
- Cortar adjetivos sem evidência, superlativos, slogans intercambiáveis e parágrafos que repetem o título. Não fabricar informalidade, erros, histórias pessoais ou depoimentos para parecer humano.
- Respeitar o vocabulário do público, o português natural e a voz da marca. Ler em voz alta para identificar frases empoladas ou repetitivas; preservar termos técnicos necessários.
- Não inventar clientes, avaliações, selos, urgência, prêmios, estatísticas, disponibilidade ou resultados. Manter lacunas explícitas e exemplos identificados até receber conteúdo aprovado.

## Imagens e detalhes

Preferir materiais próprios quando a promessa depende de pessoas, produto, equipe ou trabalho reais. Ilustrações e imagens geradas podem ter função expressiva, mas não devem se passar por documentação factual. Registrar origem, licença e uso previsto conforme [IMAGENS-E-HUMANIZACAO.md](IMAGENS-E-HUMANIZACAO.md).

Revisar anatomia, perspectiva, texto dentro da imagem, recortes, iluminação e coerência entre assets. Substituir imagens genéricas quando não ajudam a entender a oferta. Não adicionar texturas ou imperfeições falsas apenas para simular autoria humana.

## Revisão antes da entrega

- [ ] **Teste de troca de marca:** se trocar nome e logo, a página ainda serviria quase sem alterações a qualquer concorrente? Revisar os trechos intercambiáveis e registrar o que é específico deste projeto.
- [ ] **Teste de utilidade:** cada seção ajuda a entender, decidir ou agir? Remover repetições e ornamentação sem função.
- [ ] **Teste de verdade:** afirmações e imagens factuais têm origem? Demonstrações estão identificadas?
- [ ] **Teste de execução:** navegação, botões, formulários e estados funcionam? Não confundir uma captura bonita com produto concluído.
- [ ] **Teste visual:** revisar a interface renderizada em mobile e desktop, com conteúdo real, texto longo e estados relevantes. Conferir teclado, contraste e movimento reduzido.
- [ ] **Revisão editorial:** verificar precisão, voz, clareza e repetição. Registrar pendências, correções e verificações reais em DECISOES.md.

Se uma verificação falhar, corrigir ou registrar a limitação concreta antes de declarar a entrega concluída. Não trocar usabilidade por originalidade nem exigir novidade em cada componente.

## Instrução reutilizável

> Evite AI slop. Leia o briefing e o guia ANTI-AI-SLOP.md; pesquise referências e registre uma direção visual ligada ao público, à marca e à tarefa. Use conteúdo específico e verificável. Revise estruturas repetitivas, slogans vagos, imagens genéricas e efeitos sem função. Preserve padrões úteis e acessibilidade. Não invente provas sociais nem fatos para preencher lacunas. Antes de entregar, aplique os testes de troca de marca, utilidade, verdade, execução, revisão visual e editorial; informe correções e limitações reais.

## Fontes e limites

Consultadas em 30/10/2026:

- [Anthropic — Frontend Design](https://claude.com/marketplace/plugins/frontend-design): referência prática para definir intenção visual e evitar escolhas genéricas. É orientação de uma ferramenta, não evidência de que uma estética seja universalmente superior.
- [NN/g — The Custodial Era of UX: Cleaning Up After AI](https://www.nngroup.com/articles/ai-ux-debt/), Anna Kaley e Raluca Budiu, 28/08/2026: discute a dívida de UX quando a velocidade de geração supera a avaliação, e a necessidade de revisar utilidade e coerência.
- [NN/g — Generative UI and Outcome-Oriented Design](https://www.nngroup.com/articles/generative-ui/), Kate Moran e Sarah Gibbons, 22/03/2024: orienta o foco em objetivos e restrições. O artigo distingue interfaces geradas dinamicamente do uso de IA no processo de design; essa distinção deve ser preservada.

Os exemplos e testes deste guia são recomendações do FILIPE SYSTEM. Não demonstram autoria por IA nem garantem qualidade sem revisão no contexto do projeto.
