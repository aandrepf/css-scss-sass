## @use "<url>"

carrega mixins, functions e variables de outras folhas de estilo e combina CSS de várias folhas de estilos.

**Folhas de estilos carregadas por @use são chamadas de módulos**.

O Sass fornece módulos integrados cheios de funções úteis.

```scss
// @_corners.scss
$radius: 3px;

@mixin rounded { border-radius: $radius; }

// @styles.scss
@use 'src/corners' as c; // usamos 'c' como nome padrão para corners

.button {
    @include c.rounded;
    padding: 5px + c.$radius;
}

//@style.css
.button {
    padding: 8px; // somou 5px + 3px de $radius;
    border-radius: 3px; // com o include adicionou a propriedade do mixin rounded
}
```

### dica de @use

convém escolher nomes muito simples como no exemplo acima *$radius* ou $width ao escrever uma folha de estilo. Isso ajuda a evitar conflitos com outras libs, e ajuda a manter sua folha de estilo clara e fácil de ler.

não é necessário usar a extensão do arquivo que deseja carregar.

usar sempre a "/" não precisa de outras barras.

se passar "node_modules/susy/sass" como um load-path, pode usar simplesmente *@use 'susy'* para carregar o mesmo. Entretanto os **módulosa sempre carregam primeiro** em relação ao arquivo atual. Os load-paths só serão usados caso não haja nenhum arquivo relativo que corresponda ao URL do módulo.

por padrão arquivos que são apenas módulos e não devem ser compilados, começam com **_** (como _cornes.scss). São chamados de **partials** e informam ao Sass não compilar eles. Ao importar eles podemos omitir o underline.