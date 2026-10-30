# Roadmap — features para concluir o MVP

## Entrega da LP — 21/10/2026

- [x] LP pública em `/`, navegação por âncoras, projeto real do próprio site, Sobre mim e GitHub.
- [x] Direção verde, Manrope local, layout responsivo, movimento reduzido e interação de disciplinas.
- [x] Login fora da navegação pública; admin anônimo redireciona para login; noindex nas rotas restritas.
- [x] Sitemap somente da LP, robots e alias robot.txt.
- [ ] Curadoria de outros projetos reais, validação da copy pessoal e contato profissional adicional.
- [ ] Integração editorial do catálogo administrativo à LP, domínio definitivo, canonical e preview social dedicado.

Esta atualização prevalece sobre os itens históricos de scaffold abaixo. A validação e o escopo estão em [LP](LP.md).


## Administração solicitada

- [x] Implementar `/login`, `/admin` e APIs REST com autorização no servidor.
- [x] Preparar projetos, anexos privados, textos e guia de portfólio com fontes.
- [x] Implementar access/refresh tokens rotativos e encaminhamento seguro de alterações de conta ao Neon.
- [x] Validar build, tipos, schema e testes de acesso anônimo/origem externa/login móvel.
- [x] Autorizar/aplicar schema e conceder acesso à conta administrativa escolhida.
- [x] Validar persistência, mídia e sessões em branch isolada; preparar primeiro acesso por código de e-mail.
- [ ] Validar CRUD, refresh, upload e alterações de conta com banco ativado e e-mail real.
- [ ] Conectar catálogo publicado e textos ao layout público final.

Detalhes e fontes: [Admin](ADMIN.md).

Objetivo: visitante entende quem é o profissional, avalia projetos reais e encontra uma forma funcional de contato em uma LP responsiva. Itens sem marcação estão pendentes; documentação preparada não significa feature entregue.

## Preparação

- [x] Documentar arquitetura proposta, segurança, design system, banco e boas práticas.
- [x] Definir instruções para agentes e `.gitignore`.
- [x] Definir stack: Next.js com App Router, React, TypeScript estrito e CSS nativo.
- [ ] Revisar e aprovar conteúdo real, direção visual e meios de contato.
- [ ] Configurar proteção da branch principal e carregamento de `docs/AGENTS.md` na ferramenta utilizada.

## F01 — Fundação técnica

- [x] Criar scaffold Next.js com App Router e TypeScript estrito, CSS, lockfile e versões de runtime compatíveis.
- [x] Configurar Neon Postgres/Auth a pedido do usuário e validar cadastro, sessão, consulta autenticada e saída em navegador real.
- [ ] Criar scripts de tipos, lint, build e preview; CI executa checks em PR.

Aceite: instalação reprodutível pelo lockfile, build com páginas pré-renderizadas e scripts documentados sem comandos fictícios. Scaffold, tipos, build e integração Neon validados; lint e CI pendentes.

## F02 — Identidade e navegação

- [ ] Implementar hero com nome, especialidade, proposta e CTA para projetos/contato.
- [ ] Criar navegação por âncoras, link para pular conteúdo e menu móvel, se necessário.

Aceite: hierarquia de títulos coerente, navegação por teclado, foco visível, âncoras sem conteúdo oculto pelo cabeçalho e CTA com destino real. Depende de F01 e conteúdo aprovado.

## F03 — Projetos e prova de experiência

- [ ] Publicar projetos reais com contexto, contribuição pessoal, tecnologias, imagem e resultado verificável.
- [ ] Incluir links válidos quando públicos; explicar indisponibilidade quando confidenciais.

Aceite: dados separados do layout, imagens com direitos de uso e alt adequado, nenhum depoimento ou indicador inventado. Quantidade de projetos depende do material disponível. Depende de F01.

## F04 — Sobre e contato

- [ ] Apresentar biografia curta, competências e disponibilidade reais.
- [ ] Entregar links de e-mail e redes profissionais com rótulos claros.

Aceite: links testados, dados públicos revisados e acesso ao contato no celular e por teclado. Não exige formulário nem banco. Depende de F02.

## F05 — Qualidade visual e acessibilidade

- [ ] Aplicar tokens e componentes do design system.
- [ ] Revisar celular, tablet e desktop; teclado, leitor de tela em fluxo básico, contraste, zoom e movimento reduzido.

Aceite: sem rolagem horizontal em 320 CSS px, conteúdo utilizável com texto ampliado, foco não encoberto, imagens estáveis e correções dos problemas de acessibilidade identificados. Automação sozinha não prova conformidade WCAG. Depende de F02–F04.

## F06 — SEO e performance

- [ ] Configurar título, descrição, canonical, Open Graph, favicon, sitemap, robots e página 404.
- [ ] Otimizar imagens/fontes, medir carregamento e reduzir JavaScript desnecessário.

Aceite: metadados e URLs usam domínio real antes da publicação; imagens têm dimensões; registrar resultados de laboratório e limitações. Metas de campo: LCP ≤ 2,5 s, INP ≤ 200 ms e CLS ≤ 0,1 no percentil 75, por dispositivo. Dados reais dependem de tráfego após publicação. [Web Vitals](https://web.dev/articles/vitals). Depende de F05.

## F07 — Revisão e entrega

- [ ] Revisar arquivos ignorados/rastreados e conteúdo candidato a publicação; resolver achados.
- [ ] Concluir tipos, lint, build, testes pertinentes e revisão manual; preparar descrição do PR.
- [ ] Obter autorização específica para commit e para push, abrir PR e obter revisão.
- [ ] Autorizar merge/deploy, configurar domínio/HTTPS/headers e validar a LP publicada.

Aceite: PR verificável, verificações registradas, nenhuma credencial exposta, fluxo de contato funcional e revisão em produção concluída. Não existe publicação autorizada por este roadmap. Depende de F01–F06.

## Após o MVP

Formulário com entrega e proteção contra abuso, cases detalhados, CMS/blog, idioma adicional, analytics com avaliação de privacidade e persistência somente se necessária. Nenhum desses itens bloqueia o MVP.
