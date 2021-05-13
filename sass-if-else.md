# @if e @else

é escrita como **@if expressao { ... }** e controla se seu bloco é avalidado ou não (incluindo a emissão de qualquer estilo como css).

geralmente retorna true ou false;

```scss
// COMO USAR @if
@mixin avatar($size, $cicle: false) {
    width: $size;
    height: $size;

    @if $circle {
        border-radius: $size / 2;
    }
}

.square-av {
    @include avatar(100px, $circle: false);
}

.circle-av {
    @include avatar(100px, $circle: true);
}

// RESULTADO FINAL
.square-av {
    width: 100px;
    height: 100px;
}

.circle-av {
    width: 100px;
    height: 100px;
    border-radius: 50px;
}

```

```scss
// COMO USAR O @else
$light-background: #f2ece4;
$light-text: #036;
$dark-background: #6b717f;
$dark-text: #d2e1dd;

@mixin theme-colors($light-theme: true) {
    @if $light-theme {
        background-color: $light-background;
        color: $light-text
    } @else {
        background-color: $dark-background;
        color: $dark-text
    }
}

.banner {
    @include theme-colors($light-theme: true);
    body.dark & {
        @include theme-colors($light-theme: false);
    }
}

// RESULTADO FINAL
.banner {
    background-color: #f2ece4;
    color: #036;
}
body.dark .banner {
    background-color: #6b717f;
    color: #d2e1dd;
}
```