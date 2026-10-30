# Escolher e usar skills

Consulte este guia ao iniciar uma tarefa. Leia o SKILL.md da skill escolhida e as referências que ela exigir. Carregue apenas o necessário; a presença no catálogo não significa que a skill esteja instalada ou que suas ferramentas estejam conectadas.

## Escolha por tarefa

| Tarefa | Skill ou família | Condição de uso |
| --- | --- | --- |
| Planejar implementação | create-plan | Pedido explícito de plano de programação; opera em leitura e entrega o plano sem editar arquivos. |
| Questionar um plano ou design | grill-me | Invocação explícita; a versão instalada delega a grilling. Resolver essa dependência antes de considerar a skill operacional. |
| Criar ou revisar interfaces | design-taste-frontend, impeccable, emil-design-eng | Escolher a orientação adequada ao pedido e preservar identidade e componentes existentes em refinamentos. |
| Gestos e materiais de inspiração Apple | apple-design | Aplicar quando o contexto justificar; não impor essa estética a toda marca. |
| Criar movimento | animate; animate-expo | Web ou React Native/Expo, respectivamente. |
| Diagnosticar ou revisar movimento | animation-performance, review-animations, improve-animations, find-animation-opportunities | Distinguir correção, revisão pontual, auditoria e proposta. Respeitar os modos de leitura. |
| Nomear um efeito | animation-vocabulary | Consultar terminologia; não implica implementar animação. |
| Mobile web e dados extremos | mobile-native, break-ui | Verificar toque e viewport; testar conteúdo extremo conforme o escopo da skill. |
| Escolher biblioteca ou comparar protótipos | pick-ui-library, prototype | Somente quando explicitamente invocados. |
| Toasts Sonner | ask-sonner | Instalação, estados, temas e problemas da biblioteca. |
| Testar aplicação local | webapp-testing | Playwright em Python e navegador instalado; consultar ajuda dos scripts antes de usá-los. |
| Corrigir comentários de PR | gh-address-comments | Repositório Git, PR e gh autenticado; seguir a seleção de comentários exigida pela skill e o escopo autorizado. |
| Revisar prosa | stop-slop | Cortar fórmulas e frases vagas; preservar precisão, voz da marca, citações e português natural. |
| Criar diagrama editável | excalidraw-diagram | Pasta instalada: excalidraw. Ler a paleta e referências exigidas; renderização pode exigir preparação adicional. |
| Criar apresentação HTML ou converter PPT/PPTX | frontend-slides | Usar uma das cópias da skill; seguir o palco 16:9 e o ajuste de escala previstos nela. Não aplicar regras de reflow de sites aos slides. |
| Gerar ou editar bitmap | imagegen | Usar para imagens raster; preservar SVG e componentes quando a edição nativa for mais adequada. |
| Swift e concorrência | write-swift | Código Swift, migração e diagnóstico. |
| Backend Neon | neon, neon-postgres, neon-auth | Escolher projeto, SQL ou autenticação; não presumir autorização de alterar produção. |
| OpenAI e gestão de skills | openai-docs, skill-creator, skill-installer | Documentação de produto, criação ou instalação, conforme o pedido. |
| Revisão por agente | review-agent | Consultar disponibilidade e instruções; uma cópia no pacote não autoriza delegação. |
| Figma | figma-* | Escolher pelo destino: design para código, composição, biblioteca, diagrama, spec, motion, SwiftUI ou plugin. Carregar os pré-requisitos antes de chamar ferramentas. |
| Google Drive | google-drive, google-docs, google-sheets, google-slides, google-drive-comments | Escolher serviço e operação; conectores e autorização de escrita precisam estar disponíveis. |
| Pesquisa, auditoria e exploração de produto | product-design | Usar o fluxo específico do catálogo; distinguir pesquisa, crítica, variantes e implementação. |
| Sites e hospedagem | sites, sites-remix | Seguir o fluxo da ferramenta; publicação depende do escopo autorizado. |
| Pets do ChatGPT | create-pet, pets, update-pet | Para pets desse produto; não aplicar a animais reais ou imagens avulsas. |
| Integrações e CS BPO | plugin-management; instructions do CS BPO | Ler as instruções do plugin invocado e conferir conexão e permissões. |

## Instalação, cópia e disponibilidade

- `skills/` guarda o snapshot exportado e seu inventário. Essas cópias são material reutilizável; não são prova de instalação no agente atual.
- `.agents/skills/` contém instalações deste projeto. O `skills-lock.json` da raiz registra as instalações feitas pelo CLI skills; não cobre as skills globais.
- `~/.codex/skills/` contém instalações globais desta máquina. Elas não acompanham o clone do FILIPE SYSTEM.
- `skills/skills-lock.projeto.json` e `skills/INVENTARIO.json` registram o pacote original. Preserve a diferença entre histórico e instalações posteriores.
- Ao levar o kit a outra máquina, instale as skills necessárias ou copie suas pastas completas com referências, scripts e licenças. Reconfira dependências e catálogo do agente; não use caminhos pessoais deste computador como instruções portáveis.

As sete adições desta conversa estão registradas em [CATALOGO.md](../skills/CATALOGO.md). A contagem de 79 refere-se às entradas do snapshot original, inclusive cópias repetidas; não representa 79 capacidades distintas nem a soma das instalações atuais.

## Ordem de aplicação

1. Identificar objetivo, escopo autorizado, instruções existentes e alterações do usuário.
2. Escolher a skill principal e auxiliares com função distinta. Quando duas cópias tiverem o mesmo nome, escolher uma origem e registrar qual foi usada.
3. Conferir ferramentas, dependências e arquivos de apoio. Informar bloqueios reais; não declarar uma skill operacional apenas porque o SKILL.md existe.
4. Executar no modo permitido pela tarefa. Plano ou auditoria de leitura não autoriza implementação. Instalar uma skill não autoriza executá-la nem publicar seu resultado.
5. Validar a entrega conforme seu formato: navegador para interface, leitura para texto, renderização para diagrama, apresentação e controles para slides. Informar o que foi verificado e o que ficou pendente.

O pedido atual e as instruções do ambiente prevalecem sobre preferências das skills. Não solicitar permissões extras com base apenas em uma recomendação genérica da skill quando o escopo já estiver autorizado. Nenhuma skill dispensa segurança, acessibilidade ou a revisão de [ANTI-AI-SLOP.md](ANTI-AI-SLOP.md).
