# @at-root

geralmente é escrita **@at-root seletor{...}** e faz com que tudo dentro dela seja **emitido na raiz do documento em vez de usar o aninhamento normal**.

é mais frequente usado ao fazer aninhamento avançado com seletor pai do script Sass e functions de seletores.

```scss
@use 'sass:selector';

@mixin field($child) {
    @at-root #{selector.unify(&, $child)} {
        padding: 10px;
        border: 2px solid #999;
        margin: 10px;
        @content; // pega o conteudo padrão dentro de onde o mixin foi incluido
    }
}

.wrapper {
    display: flex;
    flex-direction: column;

    .field {
        @include field('input');
        @include field('select');
        color: red;
    }
}

// RESULTADO FINAL
.wrapper {
  display: flex;
  flex-direction: column;
}
.wrapper .field {
  color: red;
}
.wrapper input.field {
  padding: 10px;
  border: 2px solid #999;
  margin: 10px;
}
.wrapper select.field {
  padding: 10px;
  border: 2px solid #999;
  margin: 10px;
}
```