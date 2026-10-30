# Landing page do portfólio

Implementada em 21/10/2026 na branch `feat/portfolio-landing`. O usuário autorizou posteriormente commits por etapas e push para `main`. Nenhuma migration é executada por esta entrega.

Atualização: o refinamento posterior com Impeccable e Emil Kowalski, incluindo estabilidade do seletor, ajustes em tablet e novos tempos de movimento, está em [POLISH.md](POLISH.md). Os parâmetros e resultados abaixo registram a entrega inicial.

## Direção e conteúdo

Taste: **The name as a monument**, seed **72207545**. Inventário usado: nome Filipe Ronald; assinatura fr; áreas marketing, branding e UI/UX sem prioridade; preferência por verde; restrição ao amarelo; abertura escura; projetos claros; tipografia geométrica; personalidade sóbria/experimental; seção interna Sobre mim; GitHub filiperonald; projeto real do próprio portfólio.

Ideia: o nome Filipe Ronald se torna a estrutura tipográfica da página, reaparecendo no fechamento; o visitante explora três perspectivas sobre o mesmo projeto pelo seletor de disciplinas.

Argumento: quem é e quais áreas reúne → construção real deste portfólio e suas interfaces → apresentação pessoal e relação entre disciplinas → contato no GitHub informado. Copy completa está no Server Component `src/app/page.tsx` e em `src/data/portfolio.ts`. Não foram inventados clientes, resultados, experiência, localização ou disponibilidade. A apresentação em primeira pessoa é proposta editorial, sujeita à revisão do titular. Não existem projetos fictícios ou fotografias de terceiros.

Três redesenhos do sorteio foram necessários: hero com anel de 18–24 fotos substituído por composição tipográfica; trabalho com 10–18 nomes substituído por visual amplo de um projeto; seção Sobre com retratos substituída por fatos e parágrafo. Os materiais originais exigidos não existem. A direção prevalece sobre o recorte extremo do blueprint: o nome inteiro permanece legível, com duas linhas no celular. Paleta e tipografia seguem o briefing, com valores propostos tecnicamente.

## Implementação

- `src/app/page.tsx`: página pública pré-renderizada; CSS Module próprio.
- `src/data/portfolio.ts`: conteúdo público tipado e links existentes.
- `src/styles/tokens.css`: valores de cor, escala e movimento; tokens `--folio-*` usados pela LP.
- `src/components/portfolio-interactions.tsx`: seletor de disciplinas e IntersectionObserver para entradas CSS. Não há eventos por frame nem biblioteca de animação.
- Fonte Manrope variável local, licenciada pela SIL Open Font License; arquivo de licença ao lado da fonte. Origem: [Google Fonts / Manrope](https://github.com/google/fonts/tree/main/ofl/manrope).
- Favicon em PNG e ICO usa a mesma assinatura “fr.” do cabeçalho, renderizada com Manrope e a paleta existente. As duas rotas de ícone respondem HTTP 200 e são declaradas automaticamente pelo Next.js.
- Quatro capturas públicas do próprio site em `public/images/`: abertura, guia, cores e tipografia. Sem dados autenticados ou informações de contas. Não exigem créditos de terceiros; não há fotografia, desenho substituindo fotografia, imagem de banco ou vídeo de terceiros. A ausência de footage é intencional: não existe vídeo de trabalho real disponível e footage genérico não demonstraria este projeto.
- CSS respeita movimento reduzido e mantém conteúdo visível sem JavaScript. Navegação é nativa; o seletor mantém uma perspectiva inicial legível sem script.
- Fotos e capturas não têm links de ampliação direta; o menu de contexto e o arrasto nativo sobre imagens são bloqueados. Como os arquivos são entregues ao navegador para exibição, isso reduz salvamentos casuais, mas não impede cópia por ferramentas do navegador ou captura de tela.

A LP não consulta o banco, não publica automaticamente projetos marcados como publicados e não expõe os anexos privados do painel. A integração editorial permanece uma tarefa futura. O único contato publicado é o GitHub previamente informado. Outros projetos, biografia detalhada e contato profissional adicional aguardam conteúdo real.

## Rotas e busca

- `/`: LP indexável, sem links de acesso, conta ou administração.
- `/login`: formulário administrativo e primeiro acesso; noindex/nofollow.
- `/admin`: exige tokens administrativos e identidade Neon verificados no servidor. Sem access token e sem refresh, redireciona para `/login`; com refresh, tenta renovação em `/login?renew=1`.
- `/sitemap.xml`: somente a URL principal. Nenhuma data de atualização inventada.
- `/robots.txt`: permite página pública e exclui login/admin/conta/auth/API/guia.
- `/robot.txt`: redirecionamento permanente para o nome padronizado `/robots.txt`.

Noindex também é enviado em `X-Robots-Tag` para as rotas privadas e o guia. Robots não substitui autenticação. `SITE_URL` opcional fixa o domínio do sitemap/robots em produção; sem ele, o domínio da requisição é usado. Canonical e preview social dedicado aguardam o domínio e material definitivos.

## Verificação

Instalação reproduzível com lockfile, typecheck e build de produção aprovados. O projeto continua sem script geral de lint; o lint de Taste dos arquivos novos da LP retornou zero falhas e avisos. Oito testes Playwright de leitura/mocks aprovados: navegação, seletor por mouse/teclado, ausência de links restritos, 320–1440px, movimento reduzido, skip link, admin anônimo, noindex, sitemap/robots e os quatro testes de administração existentes. Não foi executado teste que cria usuários ou grava conteúdo no banco.

Inspector final do build de produção em 1440, 768 e 390px: **0 FAIL, 1 WARN** (sem footage, justificativa acima). Quatro imagens; títulos com no máximo duas linhas. As sete capturas finais foram abertas e revisadas. Resultados e capturas locais ficam em `.taste-skill/final/`, ignorado pelo Git. Antes: scaffold de conta, uma tela quase vazia e movimento insuficiente; depois: LP completa com aproximadamente 4,7 telas no desktop.

Revisão local dos 31 arquivos candidatos, incluindo 26 arquivos de texto, capturas e fonte. Scanner de padrões de credenciais sem achados; nenhum arquivo rastreado coincide com regras de ignore. Essa verificação limitada não garante ausência de segredos. Nenhum arquivo de ambiente privado foi publicado.

### Crítica final

ROUND 3

Seen in one second: nome Filipe Ronald em verde profundo, tipografia ampla e CTA verde-claro.

Idea (one sentence): o nome pessoal ocupa a estrutura da abertura e volta no encerramento, conectando identidade e experiência.

Live thing: seletor Marketing / Branding / UI/UX muda texto e prévia do projeto.

Layout words by section: hero=monumento tipográfico / projetos=visual amplo e detalhe editorial / sobre=fatos e parágrafo, com exploração / contato=duas colunas e assinatura.

Scores: design 7.8 · usability 8.5 · creativity 7 · content 6 → overall 7.7

Caps applied: criatividade limitada a 7, pois nome em grande escala também pode servir a outros portfólios. Conteúdo limitado pelo material real disponível; não há outros cases nem contato direto confirmado.

Top three problems (most visible first), each with the screenshot it shows in and the fix:

1. As prévias são todas do mesmo projeto (`desktop-page-01.jpg`); evolução depende de curadoria real, sem preencher com clientes fictícios.
2. O contato usa GitHub (`desktop-page-02.jpg`, `mobile-page-01.jpg`); adicionar e-mail ou rede profissional quando informado pelo titular.
3. A apresentação é breve (`tablet-page-01.jpg`); substituir a proposta editorial por trajetória e contribuições reais quando fornecidas.

Esses limites dependem de conteúdo do titular. Não impedem usar e revisar a implementação local.

## PR preparado localmente

Título: `Build Filipe Ronald portfolio landing page and isolate admin access`.

Descrição: substitui a tela de conta da rota principal por LP responsiva de marketing, branding e UI/UX, com direção verde, fonte local, estudo do próprio site e interação de disciplinas. Retira links de acesso da navegação pública, mantém administração protegida no servidor e adiciona noindex, sitemap e robots. Validação: build, tipos, oito testes de navegador e inspeção Taste em três larguras. Limites: catálogo privado ainda não integrado; demais cases, contato adicional e domínio definitivo dependem de conteúdo real. PR remoto pendente de autorização específica para commit e push.
