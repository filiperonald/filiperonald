# Tailwind CSS

Tailwind CSS 4.3.3 está integrado ao Next.js por `@tailwindcss/postcss`, com configuração em `postcss.config.mjs`. Os imports em `src/app/globals.css` disponibilizam o tema padrão e as classes utilitárias em todas as rotas. A detecção de classes está limitada a `src/`, evitando varrer skills, documentação e arquivos gerados fora da aplicação.

O Preflight do Tailwind não foi importado: o projeto mantém seu reset e os estilos existentes. Os estilos globais atuais ficam na camada `components`, permitindo que utilitários Tailwind sobrescrevam esses estilos quando usados explicitamente. CSS Modules, Bootstrap Icons e tokens próprios continuam disponíveis.

Exemplo em JSX:

```tsx
<div className="flex items-center gap-3 p-4">
  <i className="bi bi-check-circle" aria-hidden="true" />
  <span className="text-sm font-medium">Pronto para usar</span>
</div>
```

Use nomes completos de classes; evite montá-los dinamicamente como `bg-${color}-500`, pois o compilador precisa detectar as classes no código. Tailwind v4 usa configuração em CSS; não é necessário `tailwind.config.js` para esse setup.

Referência: [Tailwind com Next.js](https://tailwindcss.com/docs/installation/framework-guides/nextjs).
