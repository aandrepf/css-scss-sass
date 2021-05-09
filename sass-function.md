## @function

permite fazer operações complexas usando valores suportados pelo Sass (Number, String, Colors, Lista de Valores). Facilitam a abstração de fórmulas e comportamentos comuns de forma legível.

**@function nome_function (argumentos) { ... }**

pode conter instruções universais, bem como a regra **@return** que indica o valor a ser usado como resultado.

### curiosidade

dentro do Sass podemos usar hifen ou underline que no momento da migração ele reconhece os dois igualmente.

```scss
// @_calc.scss

@function sum($numbers...) {
    $num: 0;
    @each $number in $numbers {
        $sum: $sum + $number;
    }
    @return $sum;
}

// @style.scss
@use 'calc';

.micro {
    width: calc.sum(50px, 30px, 100px);
}

// @style.css
.micro {
    width: 180px;
}

```

### recomendações 

embora seja tecnicamente possível que as funções tenham efeitos colaterais, como definir variáveis globais, isso é fortemente não recomendado.

use mixins para efeitos colaterais e use funções apenas para calcular valores.

### regra @return

indica um valor a ser usado como resultado de uma chamada de uma funtion. Só é permitido um unico @return em cada @function.

```scss
// @_mycolor.scss
@use 'sass:color';

@function invert($color, $amount: 100%) {
    $inverse: color.change-color($color, $hue: hue($color) + 180);
    @return color.mix($inverse, $color, $amount);
}

// @style.scss
@use 'mycolor';

$primary-color: #036;
.header {
    background-color: mycolor.invert($primary-color, 80%);
}

// @style.css
.header {
    background-color: #523314;
}

```