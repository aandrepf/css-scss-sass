## @import

extende os recursos da mesma regra do CSS com a capacidade de importar folhas e Sass e Css, fornecendo acesso a mixins, functions e variables e combinando Css de várias folhas de estilo.

uma diferença entre css e sass é que a medida que renderiza sua pagina, **as importações Sass são inteiramente tratadas durente a compilação**, ao invés de fazer várias solicitações HTTP como no CSS.

no Sass o @import pode separados por vírgula importar mais de um arquivo ao invés de cada um ter seu import. Além disso, na sintaxe reduzida, os URL não precisam ter aspas.

### IMPORTANTE!!!!

a equipe do Sass **desencoraja o uso contínuo** da regra import. Eles irão gradualmente ao longo dos próximos anos eliminar e, remove-lo inteiramente da linguagem. Ao invés disso, preferir o uso da regra **@use**.

um problema do @import é que todas variables, functions e mixins se tornam globais, tornando díficil localizar a origem de onde foram definidas.


```scss
// @_list_.scss
$radius: 3px;

@mixin list-reset {
    margin: 0;
    padding: 0;
    list-style: none;
}

// @_code.scss
@import 'foundation/list';

li {
    @include list-reset;
    line-height: 0;
}

// @styles.scss
@use 'foundation/code';

// @style.css
li {
    margin: 0;
    padding: 0;
    list-style: none;
    line-height: 0;
}
```

### migrando @import para @use

o novo sistema de módulo e a regra @use tratam todos esses problemas.

a equipe do Sass tem uma ferramenta de migração que converte automáticamente a maioria do código baseado em @import para código baseado em @use em um instante. Basta apontá-lo para seus arquivos de entrada e deixar funcionando. Ele se chama **sass-migrator**.

*sass-migrator module --verbose style.scss*

*sass-migrator module --verbose --migrate-deps style.scss* (esse migra style e todos os outros que ele chama também)

Para ver as mudanças podemos usar as flags **--dry-run --verbose** (ou -nv para abreviar);