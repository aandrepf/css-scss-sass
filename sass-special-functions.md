# Funçoes Especiais Sass

css define muitas functions, e a maioria delas funciona muito bem com a sintaxe normal do Sass.

são analisados como chamadas de functions, resolvidos para funções css simples e compilados como estão para o css.

existem algumas excessões, porém, que possuem sintaxe especial que não pode ser analisada apenas como uma expressão Sass.

todas as chamadas de functions especiais retornam string sem aspas.

```scss
$font: '../fonts/Open_Sans/';

@font-face {
    font-family: 'OSRegular';
    src: url($font + 'OpenSans-Regular.ttf');
    font-weight: 400;
}

@font-face {
    font-family: 'OSLight';
    src: url($font + 'OpenSans-Light.ttf');
    font-weight: 300;
}

body {
    font-family: 'OSLight';
    font-size: 20px;
}

// RESULTADO FINAL
@font-face {
  font-family: "OSRegular";
  src: url("../fonts/Open_Sans/OpenSans-Regular.ttf");
  font-weight: 400;
}
@font-face {
  font-family: "OSLight";
  src: url("../fonts/Open_Sans/OpenSans-Light.ttf");
  font-weight: 300;
}
body {
  font-family: "OSLight";
  font-size: 20px;
}
```