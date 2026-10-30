# Design system

## Refinamento de layout e interação — 21/10/2026

Identidade preservada. Títulos passam a usar tracking até -0,04em; a assinatura fr. conserva sua composição própria. Espaçamentos da LP usam `--folio-space-section`, `--folio-space-block` e `--folio-space-group`, derivados da escala existente e fluidos por viewport. A curva `--folio-ease-ui` e o feedback de 160ms atendem aos controles; entradas editoriais usam 650ms e o nome, 800ms. A troca de disciplina por teclado é imediata. Preview estável sem recorte, links Ampliar e colapso estrutural em 960px completam a revisão. Ver [Refinamento](POLISH.md).

## Implementação da LP — 21/10/2026

A LP aplica o briefing confirmado: Filipe Ronald, marketing/branding/UI/UX, abertura verde escura e projetos claros. Proposta técnica implementada: Manrope variável local, fundo #102e25, texto claro #eff3e9, base #f3f5ef, texto #153b30, superfície #e3e9dd e acento #b9e582. Tokens `--folio-*` em `src/styles/tokens.css`; raio de mídia 24px e botões arredondados. Entradas de 750ms e título de 950ms usam transform/opacity, com conteúdo acessível sem script e movimento reduzido. O guia foi atualizado com as decisões mais recentes. Estes valores substituem a demonstração azul anterior, sem constituir aprovação de uma identidade final. Veja [LP](LP.md).


## Atualização confirmada — 21/10/2026

Este bloco prevalece sobre o briefing anterior em caso de conflito. Registra respostas do usuário; tokens e guia visual permanecem provisórios até a consolidação.

- **Marca:** Filipe Ronald.
- **Escopo:** portfólio de marketing, branding e UI/UX, sem prioridade entre áreas. Não presumir front-end como destaque nem um público comercial prioritário.
- **Composição:** abertura escura e projetos em fundo claro; verde como preferência principal, evitando amarelo.
- **Tipografia:** títulos geométricos com personalidade e textos longos neutros e legíveis. Serif e Montserrat foram citados como referências, sem escolha final de família; Montserrat é sem serifa.
- **Formas e movimento:** componentes arredondados, animações expressivas e animação de scroll; preservar acesso ao conteúdo e respeitar movimento reduzido.
- **Posicionamento desejado:** design e branding; evidências profissionais ainda não fornecidas.
- **Ações:** explorar projetos e acessar uma seção interna “Sobre mim”, conforme confirmação do usuário em 21/10/2026. Não presumir um perfil externo como destino dessa ação.
- **Personalidade confirmada:** combinação de sóbrio e preciso com criativo e experimental (alternativa A, confirmada pelo usuário em 21/10/2026).

Paleta exata, famílias tipográficas, raios e parâmetros de animação serão propostos tecnicamente, sem apresentá-los como escolhas já aprovadas.

## Briefing e fonte de decisões — 21/10/2026

Guia navegável: `/layout-guide`. Memória de decisões: [memory=ai.md](memory=ai.md).

Este documento é a especificação inicial do Brand & Design System da LP de portfólio. A estrutura foi solicitada pelo usuário; identidade, paleta final e copy ainda aguardam respostas. Distinguir sempre **definido pelo usuário**, **proposta técnica** e **pendente**. A aparência do guia demonstra a proposta existente, sem representar aprovação da marca.

### Estrutura solicitada

1. **Branding e posicionamento:** personalidade, proposta de valor, público-alvo, diferenciais, tom de voz e conceito criativo.
2. **Design system:** cores 60/30/10, tipografia, grid, espaçamento, formas, ícones, bordas, sombras e tokens.
3. **Landing page:** hierarquia visual, seções, navegação, apresentação dos projetos e chamadas para ação.
4. **Conteúdo e microcopy:** títulos, subtítulos, descrições, textos de projetos, botões, navegação e contato.
5. **Documentação e implementação:** componentes reutilizáveis, estados, responsividade, acessibilidade e regras de uso.

### Branding em definição

| Campo | Estado |
| --- | --- |
| Nome da marca | Marca pessoal confirmada; Filipe Ronald aparece no scaffold, grafia final a confirmar |
| Áreas de atuação | UI/UX, front-end e branding — definido pelo usuário em 21/10/2026; sem prioridade entre áreas |
| Público | Combinação — definido pelo usuário em 21/10/2026; composição exata e prioridade ainda não especificadas |
| Objetivo da LP | Construir autoridade — definido pelo usuário em 21/10/2026 |
| Linguagem visual | Tech — definido pelo usuário em 21/10/2026; personalidade detalhada ainda pendente |
| Base visual | Mista, com áreas claras e escuras — definido pelo usuário em 21/10/2026; distribuição entre seções pendente |
| Proposta de valor e diferenciais | Pendente; derivar de contribuições e projetos reais |
| Tom de voz | Proposta provisória: português direto, claro e sem superlativos sem evidência |
| Conceito criativo | Pendente; derivar do posicionamento, sem fixar estética antes das respostas |
| Referências e restrições | Preferência principal por verde; evitar amarelo; afinidade moderada com azul. Referência: Cnpjotas Webinars, fornecida em 21/10/2026 |

### Direção cromática após o briefing

Referência fornecida e inspecionada no navegador: [Cnpjotas Webinars](https://cnpjotas-webinars-hazel.vercel.app/). Verdes profundos observados: `#173f35` e `#0f332c`; superfícies claras: `#f6f8f2` e `#e1ebe4`. São cores da referência, não uma paleta aprovada. O amarelo/âmbar da referência não será adotado como direção, conforme preferência do usuário.

Proposta a desenvolver: base mista com campos claros e verde profundo, assinatura em verde, sem amarelo decorativo. Azul é opcional, sem competir com o verde. Os tokens azuis e exemplos claros existentes abaixo permanecem como demonstração técnica anterior até a consolidação da paleta e dos estados de contraste.

Para construir autoridade, propõe-se apresentar estudos de caso com problema, raciocínio, decisões de design, execução e contribuições verificáveis nas três áreas. O conteúdo real ainda precisa ser informado.

### Regra 60/30/10 — definida

| Proporção | Papel | Aplicação |
| --- | --- | --- |
| 60% | Cor dominante / base | Fundo da página, áreas amplas e respiro |
| 30% | Cor secundária / estrutura | Texto, títulos, navegação, rodapé e áreas estruturais |
| 10% | Acento / destaque | CTA principal, links importantes e indicadores pontuais |

É uma referência de composição global, não uma obrigação matemática em cada seção ou componente. Não determina os hexadecimais finais nem substitui a avaliação de contraste.

## Status e direção

Especificação inicial para implementação, ainda sem protótipo validado. A LP deve priorizar nome, especialidade, trabalho demonstrável e contato. Direção visual proposta: base neutra, tipografia legível, uma cor de destaque e imagens reais dos projetos. Ajustar a identidade ao material do portfólio antes de implementar o visual final.

## Tokens propostos

Centralizados em `src/styles/tokens.css`, consumidos pelo guia. O restante do scaffold ainda usa estilos anteriores; a migração global depende da identidade final. Componentes novos devem consumir as variáveis, sem duplicar valores arbitrários.

| Grupo | Tokens iniciais | Uso |
| --- | --- | --- |
| Cor | `--color-bg: #fafaf9`, `--color-surface: #ffffff` | Fundo e superfícies |
| Texto | `--color-text: #18181b`, `--color-muted: #52525b` | Conteúdo e apoio |
| Ação | `--color-accent: #1d4ed8`, `--color-on-accent: #ffffff` | Links, CTA e foco |
| Bordas | `--color-border: #d4d4d8` | Separação decorativa; validar outro tom para controles |
| Tipografia | Sans do sistema; pesos 400, 500 e 700 | Evitar downloads inicialmente |
| Escala | 0,875; 1; 1,25; 1,5; 2; 3; 4 rem | Texto e títulos fluidos |
| Espaço | 0,25; 0,5; 0,75; 1; 1,5; 2; 3; 4; 6 rem | Ritmo de layout |
| Layout | Conteúdo até 72 rem; texto até 65 ch | Leitura e alinhamento |
| Forma | Raios 0,25 e 0,5 rem | Controles e imagens |
| Movimento | 120–200 ms para feedback simples | Preferir opacity/transform |

Tokens adicionais implementados: `--color-accent-hover: #1e40af`, `--color-control-border: #71717a`, `--font-body`, `--text-small`, `--text-body`, `--text-lead`, `--text-section`, `--text-display`, `--space-{1,2,3,4,6,8,12,16,24}`, `--content-max`, `--text-max`, `--radius-small`, `--radius-control` e `--motion-feedback: 160ms`. Os sufixos de espaço representam múltiplos de 4 px na base de 16 px.

O guia usa uma escala efetiva de 0,875 / 1 / 1,25 / 1,5–2 / 2–4 rem. Títulos fluidos; entrelinha de corpo 1,5. Grid proposto: até 72 rem, margens de 24 px e 16 px até 640 px; uma coluna no celular e duas quando o conteúdo couber. Raios de 4 e 8 px. Sem sombras em repouso; sombras futuras restritas a camadas flutuantes. Ícones futuros devem usar uma família consistente, ter função e nome acessível quando interativos.

## Estrutura e copy da LP — proposta pendente

| Seção | Conteúdo necessário | Estado |
| --- | --- | --- |
| Navegação | Nome, projetos, sobre e contato | Rótulos e destinos finais pendentes |
| Apresentação | Nome, especialidade, proposta de valor e CTA prioritário | Briefing pendente |
| Projetos | Título, problema, contribuição, decisões, tecnologias e resultados verificáveis | Material real pendente |
| Sobre | Trajetória e diferenciais comprováveis | Informações pendentes |
| Contato e fechamento | Convite alinhado ao objetivo, e-mail e redes confirmados | Destinos pendentes |

A ordem será revista conforme o argumento e as evidências disponíveis. Não criar depoimentos, métricas ou clientes fictícios. Os textos do guia são documentação e exemplos tipográficos; não constituem copy final da LP.

## Questionário para consolidar a identidade

1. Respondido: UI/UX, front-end e branding. Nenhuma área foi indicada como prioritária.
2. Respondido: combinação de públicos. Composição exata e prioridade ainda não especificadas.
3. Respondido: linguagem tech.
4. Respondido: base mista, combinando áreas claras e escuras.
5. Respondido: marca pessoal. Nome exato de apresentação ainda a confirmar.
6. Respondido: construir autoridade.
7. Respondido: verde como preferência principal; evitar amarelo; afinidade moderada com azul. Referência: Cnpjotas Webinars.
8. Respondido: projetos do [GitHub pessoal filiperonald](https://github.com/filiperonald); inclusão posterior de links para imagens, vídeos, PowerPoints, planilhas e marcas próprias. Curadoria, contribuições e contatos adicionais ainda pendentes.

## Conteúdo multimídia e projetos

Fonte inicial definida: GitHub pessoal `filiperonald`. A consulta à API pública em 21/10/2026 retornou apenas o repositório `filiperonald`, sem descrição. Projetos privados ou de outras fontes não podem ser inferidos dessa listagem. A seleção de destaques depende da curadoria dos trabalhos reais.

O sistema deve acomodar repositórios/sites, imagens, vídeos, apresentações PowerPoint, planilhas e identidades de marca. Cada item terá título, categoria, resumo, contribuição e destinos opcionais identificados pelo formato. Usar “Ver código”, “Assistir ao vídeo”, “Ver apresentação” ou “Abrir planilha”, conforme o destino. Não criar links ou prévias fictícias enquanto o material futuro não for fornecido.

Imagens: texto alternativo conforme a função. Vídeos: legendas ou alternativa textual, reprodução sob controle do visitante. Apresentações e planilhas: resumo em HTML para contextualizar o material; downloads com formato e tamanho quando conhecido. Uma marca pode ser apresentada como estudo de caso, com contexto, conceito e aplicações reais. Esses requisitos documentam a evolução do portfólio; não implicam integração automática, upload ou incorporação implementados.

Após as respostas: registrar na memória, consolidar posicionamento e conceito, justificar a paleta e tipografia, atualizar tokens e guia, e desenvolver a copy completa. Não promover proposta a decisão aprovada sem evidência na conversa.

As cores são propostas; validar contraste em todas as combinações e estados antes de publicar. Cor de borda decorativa não garante contraste para identificar um controle.

## Componentes e estados

- Header: marca textual, navegação clara e acesso ao contato. Se houver menu recolhível, botão com nome, `aria-expanded`, foco previsível e fechamento por Escape.
- Links e botões: âncoras navegam; botões executam ações. Estados normal, hover, foco e ativo; desabilitado apenas quando houver motivo real. Não depender só de cor para comunicar ação.
- Projeto: título, contexto, contribuição, tecnologias e imagem; link somente quando disponível. Evitar links aninhados e conteúdo essencial restrito a hover.
- Seção: espaçamento consistente, título descritivo e ordem semântica.
- Contato e footer: destinos reais com rótulos compreensíveis; ícones com nome acessível.
- Formulários e toasts ficam fora do MVP; seus estados devem ser especificados se o escopo mudar.

## Regras de acessibilidade e responsividade

Alvo: WCAG 2.2 nível AA. Contraste de texto de pelo menos 4,5:1, ou 3:1 para texto grande conforme a definição WCAG; elementos visuais necessários à identificação de controles precisam de contraste apropriado. Foco visível e não oculto. Usar alvos confortáveis de aproximadamente 44 × 44 CSS px quando possível e respeitar os critérios/exceções de tamanho mínimo da WCAG 2.2.

Começar em uma coluna e introduzir colunas conforme o conteúdo couber. Revisar em 320, 375, 768, 1024 e 1440 CSS px, além de zoom e orientação paisagem. Evitar alturas fixas para texto, preservar quebra de URLs e garantir áreas de toque sem depender de hover.

Usar um `h1`, regiões semânticas e alt conforme o propósito da imagem; decorativas têm alt vazio. Respeitar `prefers-reduced-motion`; não esconder conteúdo atrás de animação de entrada. Nenhum carrossel automático ou efeito obrigatório para acessar o portfólio.

Referência normativa: [WCAG 2.2 — W3C](https://www.w3.org/TR/WCAG22/). Revisão automatizada deve ser acompanhada por uso manual de teclado e tecnologias assistivas.
