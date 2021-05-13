## @mixin

eles permitem que definamos estilos que podem ser reutilizados em sua folha de estilo. Tornam mais fácil evitar o uso de classes não semânticas e distribuir coleções de estilos em libs.

A sintaxe pode ser **@mixin nome {...}** ou **@mixin nome(args) {...}**

## @include

quando queremos usar os mixins usamos essa regra. Sua sintaxe é escrita **@include nome-mixin** ou **@include nome_mixin (args)**.

```scss
// @_list.scss
@mixin reset-list {
    margin: 0;
    padding: 0;
    list-style: none;
}

@mixin horizontal-list {
    @include reset-list;
    li {
        display: inline-block;
        margin: {
            left: 2px;
            right: 2em;
        }
    }
}

// @style.scss
@use 'list';

nav ul {
    @include list.horizontal-list;
}

// @style.css (FINAL)
nav ul {
    margin: 0;
    padding: 0;
    list-style: none;
}

nav ul li {
    display: inline-block;
    margin-left: -2px;
    margin-right: 2em;
}
```

## Curiosidades

os nomes de mixins, assim como todos os identifiers do Sass, tatam hífen e traço como identicos. Ex.: reset-list e reset_list referem-se ao mesmo mixin.