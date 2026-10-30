# Ícones

Bootstrap Icons 1.13.2 está instalado via pnpm. O CSS da fonte é importado no layout raiz do Next.js e fica disponível em todas as rotas, com arquivos servidos pelo próprio aplicativo.

Uso em JSX:

```tsx
<i className="bi bi-github" aria-hidden="true" />
```

Com texto visível, o ícone é decorativo. Quando um botão ou link contiver somente um ícone, fornecer um nome acessível no controle:

```tsx
<button type="button" aria-label="Fechar">
  <i className="bi bi-x-lg" aria-hidden="true" />
</button>
```

O tamanho acompanha `font-size` e a cor acompanha `color`. Foi instalado apenas o pacote de ícones; o CSS e o JavaScript de componentes do Bootstrap não foram adicionados.

Catálogo e nomes das classes: [Bootstrap Icons](https://icons.getbootstrap.com/).
