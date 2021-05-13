# for

pode ser escrita:

**@for variable from expression to expression {...}** ou

**@for variable from expression through expression {...}**

ela conta para cima ou para baixo a partir de um número (o resultado da primeira expressão) para outro (o resultado da segunda expressão) e avalia um bloco para cada número intermediário.

cada número ao  longo do caminho é atribuído a um determinado nome de variável. Se **to** for usado, o número final é excluído; se **through** é usado o número é incluído;

```scss
@use 'sass:color';

$base-color: #036;

@for $i from 1 through 3 {
    ul:nth-child(3n + #{$i}) {
        background-color: color.adjust($base-color, $lightness: $i * 15%);
    }
}

// RESULTADO FINAL
ul:nth-child(3n+1) {
  background-color: #0059b3;
}
ul:nth-child(3n+2) {
  background-color: #0080ff;
}
ul:nth-child(3n+3) {
  background-color: #4da6ff;
}
```
