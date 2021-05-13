# @debug

as vezes, é util ver o valor de uma variável ou expressão enquanto desenvolvemos uma folha de estilo.

a regra **@debug expressao** imprime o valor dessa expressão, junto com o nome do arquivo e o número da folha.

```scss
@mixin inset-divider-offset($offset, $padding) {
    $divider-offset: (2 * $padding) + $offset;
    @debug "divider offset: #{$divier-offset}";

    margin-left: $divider-offset;
    width: calc(100% - #{$divider-offset});
}
```