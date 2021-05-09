## @forward "<url>"

carrega uma folha de estilo Sass junto com seus mixins, functions e variables quando sua folha de estilo é carregada usando @use. Torna possível organizar libs Sass em muitos arquivos, enquanto permite que seus usuarios carreguem um único arquivo de entrada.

carrega o módulo exatamente como @use, mas **torna membros públicos do módulo carregado disponíveis para os usuários do seu módulo como se eles tivessem sido definidos diretamente no seu módulo**. No entanto, esses membros não estam disponíveis em seu módulo - se quiser, precisará escrever uma regra @use também. Ele carrega o módulo uma vez.

```scss
// @_list.scss
@mixin list-reset {
    margin: 0;
    padding: 0;
    list-style: none;
}

// @bootstrap.scss
@forward 'src/list'; // trazer o list para bootstrap como parte desse módulo

// @style.scss
@use 'bootstrap';

li {
    @include bootstrap.list-reset;
}

// FINAL: @style.css
li {
    margin: 0;
    padding:0;
    list-style: none;
}
```

### adicionando prefixos

máodulos com namespace, curtos e simples são mais legíveis, mas podem não fazer sentido fora do módulo em que estam definidos. Então, o @forward tem a opção de adicionar um prefixo extra para todos os membros que ele encaminha.

é escrito como @forard <url> as prefixo-* e adicionad o prefixo fornecido ao início de cada mixin, function ou variable encaminhado pelo módulo. Se o módulo define um membro chamado reset e é encaminhado como list-*, as folhas de estilo seguintes irão se referir a ele como list-reset.

```scss
// @_list.scss
@mixin reset {
    margin: 0;
    padding: 0;
    list-style: none;
}

// @bootstrap.scss
@forward 'src/list' as list-*; // usando prefixo para o módulo

// @style.scss
@use 'bootstrap';

li {
    @include bootstrap.list-reset;
}

// FINAL: @style.css
li {
    margin: 0;
    padding:0;
    list-style: none;
}
```

### controlando visibilidade

```scss
// @_list.scss
@mixin reset {
    margin: 0;
    padding: 0;
    list-style: none;
}
@mixin horizontal {
    li {
        @include reset;
        display: inline-block;
        margin: {
            left: -2px;
        }
    }
}

// @bootstrap.scss
@forward 'src/list' as list-* hide reset; // não deixa usar o reset diretamente 

// @style.scss
@use 'bootstrap';

li {
    @include bootstrap.list-horizontal;
}

// FINAL: @style.css
li {
    margin: 0;
    padding:0;
    list-style: none;
}
```