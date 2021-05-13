## @extend

ao projetar uma página, há casos em que uma classe deve ter todos os estilos de outra classe, bem como seus próprios estilos específicos.

a metodologia **BEM** (bloco, elemento e modificador) encoraja classes que vão nos mesmos elementos que blocos ou classes de elementos.

isso pode criar um HTML desordenado, estará sujeito a erros por esquecer de incluir as duas classes e pode trazer preocupações de estilo não semantico para o HTML.


### metodologia BEM (Block, Element, Modifier)

são as bases e também são as categorias nas quais vamos dividir os elementos.

```html
<header class="header">
    <h1 class="header__title">Bem Vindo</h1>
    <button class="header__login">Login</button>
</header>
```

no exemplo acima, a primeira classe será o **Block** : .header

os **Element**, usamos os 2 underlines após o nome do bloco: .header__title, .header__login

os **Modifiers**, usamos os 2 traços, no bloco ou elemento: .header__title--higlight, .header__login--active

```html
<div class="error error--serious">
    Erro Fatal! Fechando Aplicação.
</div>
```

```scss
.error {
    border: 1px #fdd;
    background-color: #fdd;
}

.error--serious {
    border-width: 3px;
}

// RESOLVENDO COM EXTEND
.error {
    border: 1px #fdd;
    background-color: #fdd;

    &--serious {
        @extend .error;
        border-width: 3px;
    }
}

// RESULTADO FINAL
.error, .error--serious {
    border: 1px #fdd;
    background-color: #fdd;
}
.error--serious {
    border-width: 3px;
}
```

### diferença entre @extend e @mixin

os mixins copiam estilos para a regra de estilo atual, já o extend **atualiza as regras de estilo que contêm o seletor estendido para que também contenham o seletor estendido**. Assim ele faz uma unificação inteligente: 

*Ele nunca gera seletores como #principal#rodape que não podem corresponder a nenhum elemento*

isso garante que os seletores complexos sejam intercalados para que funcionem independentemente da ordem em que os elementos HTML são aninhados.

extends corta seletores repetidos o máximo possível.

extend sabe quando um seletor corresponde a tudo o que o outro faz e pode combiná-los.

lida de forma inteligente com combinadores, seletores universais e pseudo-classes que contém seletores.

```scss
.content nav.sidebar {
    @extend .info;
}

// p é compativel com nav, será ignorado
p.info {
    background-color: #dee9fc;
}

// Sass irá combinar .content dentro de .guide
.guide .info {
    border: 1px solid rgba(#000, 0.8);
    border-radius: 2px;
}

// Sass vai aplicar automaticamente main.content também
main.content .info {
    font-size: 0.8em;
}

// RESULTADO FINAL
p.info {
    background-color: #dee9fc;
}

.guide .info, .guide content nav.sidebar,
.content .guide nav.sidebar {
    border: 1px solid rgba(#000, 0.8);
    border-radius: 2px;
}

main.content .info, main.content nav.sidebar {
    font-size: 0.8em;
}