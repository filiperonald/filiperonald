# Security — segurança por projeto

Guia de implementação e revisão, não certificação. Ajustar à arquitetura, exposição e dados tratados. Consultar fontes atuais em decisões sensíveis.

## Modelo de ameaça

Listar ativos (dados, sessões, arquivos), atores (público, usuário, admin), fronteiras (navegador, servidor, banco, terceiros) e abusos prováveis. Identificar operações de maior impacto e testes de isolamento.

## Segredos e dependências

- Segredos somente no servidor e no gerenciador do ambiente; nada em código, Markdown, assets ou logs. Tudo enviado ao navegador é público.
- `.env.example` contém placeholders. `.gitignore` não elimina segredo já rastreado.
- Após vazamento, revogar/rotacionar primeiro e avaliar alcance; apagar arquivo não invalida credencial.
- Menor privilégio, lockfile e revisão de origem/scripts de dependências. Avaliar vulnerabilidade pelo caminho afetado; evitar upgrades forçados sem revisão.

## Identidade e autorização

Preferir provedor consolidado e SDK oficial compatível. Não inventar criptografia ou armazenamento próprio de senhas. Autenticar no servidor e autorizar cada operação por recurso, proprietário, papel e tenant. Negar por padrão. Esconder um botão não protege API.

Cookies de sessão: HttpOnly, Secure em produção e SameSite adequado ao fluxo. Expiração, renovação e revogação conforme o provedor. Proteger mutações autenticadas por cookie contra CSRF, validando origem e/ou token conforme arquitetura. CORS não substitui autorização.

Limitar tentativas de login e abuso. Evitar mensagens que revelem contas desnecessariamente. Cache privado não pode vazar dados entre usuários.

## Entradas, APIs e banco

Validar esquema, tipos, limites e tamanho no servidor. Queries parametrizadas; campos graváveis definidos explicitamente para evitar mass assignment. Paginação e limites protegem custo. Erros públicos sem SQL, stack ou infraestrutura.

Fetch de URL fornecida pelo usuário exige defesa contra SSRF: protocolos/destinos permitidos, bloqueio de redes internas e atenção a resolução DNS e redirects. Não assumir que validar a URL inicial basta.

## XSS, headers e uploads

Evitar HTML bruto. Quando necessário, sanitizar com ferramenta mantida e política de URLs. HTTPS, nosniff, Referrer-Policy e Permissions-Policy coerentes. Construir CSP para recursos reais, observar relatórios e aplicar. Avaliar HSTS e subdomínios antes de ativar.

Uploads: autorização, limites de bytes/quantidade, extensão, MIME e assinatura quando aplicável. Gerar nomes próprios, não confiar no nome enviado e separar armazenamento de execução. Proteger downloads privados. HTML/SVG ativo não confiável não deve ser servido livremente na origem principal; avaliar conversão, sanitização, sandbox ou anexo. Antivírus conforme o risco.

## Dados e operação

Coletar o mínimo, definir finalidade, retenção, acesso e descarte. Logs e backups também precisam de proteção. Conta de banco com menor privilégio. Testar restauração e rollback em ambiente isolado. Migrations e produção seguem o escopo autorizado.

## Testes objetivos

Em ambiente autorizado, testar: anônimo, usuário A tentando acessar B, tenant cruzado, papel insuficiente, sessão expirada, CSRF, entrada malformada, upload proibido, abuso de frequência e dados sensíveis em respostas/cache/logs. Registrar resultado e limitações.

Fontes consultadas em 30/10/2026: [OWASP Authorization](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html), [File Upload](https://cheatsheetseries.owasp.org/cheatsheets/File_Upload_Cheat_Sheet.html) e [Input Validation](https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html).
