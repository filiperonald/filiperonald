# Performance

Definir orçamento conforme público/dispositivo. Priorizar carregamento principal, resposta ao input e estabilidade visual. Conferir definições e metas atuais de Core Web Vitals na documentação antes de contratos.

Reservar espaço de mídia, otimizar imagens e evitar vídeo automático desnecessário. Reduzir famílias/pesos de fontes e preservar licenças. Usar a stack existente, reduzir JavaScript cliente e carregar funcionalidades secundárias sob demanda. Não instalar biblioteca grande para um fade.

Evitar loops permanentes, blur amplo e camadas GPU indiscriminadas. Medir frames, layout, paint e tarefas longas no DevTools. Nenhum efeito deve prejudicar scroll ou digitação.

Medir em build equivalente a produção, com perfil mobile/rede limitada. Lighthouse é diagnóstico de laboratório; dados de campo respondem outra pergunta. Registrar configuração e limitações. Em rede lenta, conteúdo e tarefa principal continuam acessíveis.
