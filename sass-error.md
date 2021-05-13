# @error

podemos monitorar erros no script sass.

ele ajuda o desenvolvedor/designer a identificar o erro antes que ele estoure no layout.

a sintaxer **@error expression** é uma string junto com um rastreamento de pilha indicando como o mixin ou function atual foi chamado. O sass para de compilar e diz a qualquer sistema que ocorreu um erro.

```scss
@mixin reflexive-position($property, $value) {
    @if $property != left and $property != right {
        @error "A propriedade #{$property} precisa ser left ou right.";
    }

    $left-value: if($property == left, initial, $value);
    $right-value: if(property == right, $value, initial);

    left: $left-value;
    right: $right-value;
}

.sidebar {
    @include reflexive-position(top, 12px);
    //       ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    // Error: A propriedade top precisa ser lef ou right;
}
