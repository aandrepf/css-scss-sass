# @each

facilita a emissão de estilos ou avaliação de código para cada elemento de uma **lista** ou cada para de um **map**. È ótimo para elementos repetitivos que tem apenas algumas variações entre eles.

geralmente escrito **@each variable in expression {...}**, onde a espressão retorna uma lista. O bloco é avaliado para cada elemento da lista, por sua vez, que é atribuido ao nome de variável fornecido.

```scss
// @each como LISTA
$sizes: 40px, 50px, 80px;

@each $size in $sizes {
    .icon-#{$size} {
        font-size: $size;
        height: $size;
        width: $size;
    }
}

// RESULTADO FINAL
.icon-40px {
    font-size: 40px;
    height: 40px;
    width: 40px;
}
.icon-50px {
    font-size: 50px;
    height: 50px;
    width: 50px;
}
.icon-80px {
    font-size: 80px;
    height: 80px;
    width: 80px;
}
```

```scss
// @each como MAP
$sizes: ('xs': 50px, 'sm': 100px, 'md': 200px);

@each $key, $value in $sizes {
    .#{$key} {
        width: $value;
        height: $value;
        border-radius: $value / 2;
    }
}

// RESULTADO FINAL
.xs {
  width: 50px;
  height: 50px;
  border-radius: 25px;
}

.sm {
  width: 100px;
  height: 100px;
  border-radius: 50px;
}

.md {
  width: 200px;
  height: 200px;
  border-radius: 100px;
}
```