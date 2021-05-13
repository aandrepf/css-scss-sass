# @warn

ao escrever mixins e function, podemos alertar os usuário a passar certos argumentos ou valores, pois podem estar passando argumentos legados que podem estar obsoletos.

ao contrário da regra @error **ela não interrompe o sass inteiramente**.

```scss
$default-prefixes: webkit, moz, ms, o;

@mixin prefix($property, $value, $prefixes) {
    @each $prefix in $prefixes {
        @if not index($default-prefixes, $prefix) {
            @warn 'Prefixo desconhecido #{$prefix}.';
        }

        -#{$prefix}-#{$property}: $value;
    }
    #{$property}: $value;
}

.tilt {
    // Digitamos errado wekbit em vez de webkit
    @include prefix(transform, rotate(15deg), wekbit ms);
}