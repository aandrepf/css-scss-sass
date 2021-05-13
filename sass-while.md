# @while

escrita como **@while expression {...}**, avalia seu bloco se sua expressão retornar verdadeira. Isso continua até que a expressão retorne false.

deve ser usado para situações mais complexas, por ser mais pesado que @for e @each.

```scss
@function scale-below($value, $base: 16px, $ratio: 1.618) {
    @while $value > $base {
        $value: $value / $ratio;
    }

    @return $value;
}

$normal: 50px;

p {
    font-size: $normal;
    sup {
        font-size: scale-below($normal);
    }
}

// RESULTADO FINAL
p {
  font-size: 50px;
}
p sup {
  font-size: 11.80414274px;
}
```