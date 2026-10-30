# Fontes e atualização

Snapshot: 30/10/2026. Valores visuais são pontos de partida, não regras aprovadas para outras marcas.

## Fontes primárias

- [OWASP Authorization](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html)
- [OWASP File Upload](https://cheatsheetseries.owasp.org/cheatsheets/File_Upload_Cheat_Sheet.html)
- [OWASP Input Validation](https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html)
- [OWASP Secrets Management](https://cheatsheetseries.owasp.org/cheatsheets/Secrets_Management_Cheat_Sheet.html)
- [W3C C39](https://www.w3.org/WAI/WCAG22/Techniques/css/C39.html)
- [W3C contraste](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html)
- [W3C alvos](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html)
- [Chrome Motion](https://developer.chrome.com/docs/modern-web-guidance/guides/ui-behaviors/motion)

Guias de segurança e movimento informados por pesquisa nas referências pertinentes. Revalidar fontes, APIs, licenças e recomendações ao iniciar cada projeto.

## Pesquisa sobre AI slop

Referências consultadas em 30/10/2026 e limites de aplicação registrados em [ANTI-AI-SLOP.md](guias/ANTI-AI-SLOP.md): [Anthropic — Frontend Design](https://claude.com/marketplace/plugins/frontend-design), [NN/g — The Custodial Era of UX](https://www.nngroup.com/articles/ai-ux-debt/) e [NN/g — Generative UI and Outcome-Oriented Design](https://www.nngroup.com/articles/generative-ui/). As regras do kit são uma síntese editorial, não um detector de autoria por IA.

## Origem local

Projeto filiperonald-site/projetos. referencia-portfolio/ preserva Markdown e tokens originais, inclusive histórico e contradições; não comprova o estado de segurança ou produção do site.

Skills preservam os arquivos originais. skills/INVENTARIO.json registra origem, destino e SHA256 do SKILL.md. skills/skills-lock.projeto.json é o lockfile original, que lista menos entradas que as pastas existentes; não representa um lockfile das 79 cópias.

Este pacote não exporta .env, credenciais, banco ou dados de runtime. Referências a nomes de variáveis e exemplos de ferramentas podem existir nas instruções. Plugins copiados não transferem autenticação ou disponibilidade das ferramentas.

## Instalações posteriores ao snapshot

O [catálogo](skills/CATALOGO.md) registra sete adições e seus repositórios de origem. Duas ficam em `.agents/skills/`; cinco ficam na instalação global do Codex e não foram exportadas para `skills/`. O lockfile da raiz cobre apenas as duas instalações feitas pelo CLI skills. A versão histórica de create-plan e a dependência pendente de grill-me estão indicadas no catálogo.
