# Pré-processador de CSS

| Sass | https://sass-lang.com |
| Sass Install | https://sass-lang.com/install |
| Sass Guide | https://sass-lang.com/guide |
| Sass Doc | https://sass-lang.com/documentation |

| Pravatar | https://pravatar.cc/ |

| Compiler Hero | https://marketplace.visualstudio.com/items?itemName=Wscats.eno |
| Live Sass Compiler | https://marketplace.visualstudio.com/items?itemName=glenn2223.live-sass |

```json
//@setting.json (VSCODE)
"liveSassCompile.settings.formats": [
	{
		"format": "expanded",
		"extensionName": ".css",
		"savePath": "./css"
	}
]
```

Sass é uma linguagem de folha de estilos de nível profissional mais madura, estável e poderosa.

Sass é compatível com todas as versões de CSS. Tem sido por mais de 14 anos escolhido e apoiado pela indústria como principal linguagem de extensão do CSS.

## Porque utilizar Sass?

Os pré-processadores são linguagens de script que estendem os recursos padrão de CSS.

É permitido usar lógica no código CSS, como variáveis, aninhamento, herança, mixins, funções e operações matemáticas.

Façilitam a automatização de tarefas repetidtivas, reduzem erros e inchaços de código, criam fragmentos de código reútilizáveis e garantem compatibilidade com versões anteriores.

## Outros pré-processadores

Cada pré-processador tem sua sintaxe que é compilada em CSS regular. Atualmente temos 3 pré-pocessadores estáveis: Sass, Less, Stylus e Styled Components.

Usando CSS normal (extensão **.css**)

```css
body {
	margin: 0;
	background-color: black;
}
body header {
	background-color: #fff;
	color: black;
	height: 64px;
	padding: 8px;
}
body header a {
	text-decoration: none;
}
```

Com Sass (extensão dos arquivos **.scss**)

```scss
/* exemplo de Nesting */
body {
	margin: 0;
	background-color: black;
	
	header {
		background-color: #fff;
		color: black;
		height: 64px;
		padding: 8px;
		
		a {
			text-decoration: none;
		}
	}
}
```

E temos ainda os com a extensão **.sass**
```sass
/* Hierarquia */
body
	margin: 0;
	background-color: black;
	header
		background-color: #fff;
		color: black;
		height: 64px;
		padding: 8px;
		a
			text-decoration: none;
```


## Instalando o Sass

Instalar via npm usamos o comando **npm install -g sass**.

Depois de instalado, podemos monitorar um arquivo ou diretório com a flag **--watch**. Ela avisa o Sass sempre que um arquivo ou pasta for alterado, e irá recompilar o arquivo Sass.

Para ativar o monitoramento de um arquivo sem ter que fazer individualmente, basta adicionar o comento --watch:

    sass --watch input_file.scss output_file.scss

Ou podemos monitorar um diretório. Para gerar um código correspondente a outro diretório, basta utilizar o sinal de : (dois pontos).

    sass --watch src/sass:dist/assets/css

No exemplo acima o sass irá monitorar o diretório src/sass, buscando por alterações, e irá compilar o CSS final para a pasta dist/assets/css.

## nesting (aninhamento)

Tem como objetivo deixar a vida do dev mais facil com organização de código.

Com ele evitamos repetição de seletores, podendo escrever um bloco de estilo dentro de outro bloco. É sempre importante avaliar o uso do nesting, pois nem sempre é necessário o uso do mesmo evitando uma especificidade muito complexa.

### lista de seletores

é possível também fazer aninhamento de lista de seletores separados por vírgula.

### combinadores de seletor

podemos também usar nesting que usem combinadores como: 

- Descendente ( ' ' )
- Filho Direto (>)
- Irmão Geral ( + )
- Irmão Adjacente ( ~ )

é possível colocar o combinador no final do seletor pai, no ínicio do seletor filho ou mesmo sozinho entre os dois.


## variáveis

sempre que for necessário utilizar um valor em vários lugares, usamos variáveis. No sass nomeamos uma variavel iniciando com **$nome_da_variavel** e então atribuímos valor à essa variavel definida.

### sass variables X css variables

- no sass as variaveis são totalmente compiladas gerando static code. Ja no css são mantidas no arquivo.
- em css variaveis podem ter n valores para n elementos, as de sass sempre possuirão o mesmo valor.
- em sass são **imperativas**, assim usamos e podemos alterar seu valor. Em css são **declarativas**, ou seja, se alterado o valor afeta todos os pontos onde está declarada.

```scss
$variavel: 10px;
.class { value: $variavel; }
```

em sass os *hifens* e *underscores* são tratados de maneira identica. O que siginifica que $font-size e $font_size referem-se a mesma variável.

### valor padrão !default

ao se atribuir um valor a uma variável, se ela já tiver um valor, o mesmo é sobrescrito. Com o Sass convém permitir que usuários configurem as variáveis antes de usá-las para gerar Css.

para isso o sass tem o **!default**. Isso atribui um valor apenas se a variável não for definida ou seu valor é **null**. Caso contrário, o valor existente será usado.

variáveis com !default, pode ser configuradas ao carregar um módulo com a regra **@use**. Libs Sass costumas usar variáveis !default para permitir que seus users configurem o CSS da lib.

```scss
// SINTAXE: @use url with(variavel: valor, variavel: valor)

// @lib.scss
$black: #000 !default;
$border-radius: 0.25rem !default;

code {
	border-radius: $border-radius;
	background-color: $black;
}

// @style.scss
@use 'lib' with(
	$black: #222, // só permite novos valores se lá em lib existir o !default
	$border-radius: 0.1rem
);

// @style.css (COMPILADO)
code {
	border-radius: 0.1rem;
	background-color: rgb(34, 34, 34);
}
```

### variáveis nativas e escopo de variáveis

**variáveis nativas** = conhecidas também como *built-in*, não podem ser alteradas atuando como constantes. Elas se encontram em vários módulos dentro do SASS.

```scss
@use 'sass:math' as math;

math.$pi: 0;
// output: Não é possível atribuir valor a uma variável interna. Erro.
```

**escopo de variáveis** = as declaradas no nível superior de um css são globais, ou seja, podem ser acessadas em qualquer lugar no módulo depois de declaradas. Aquelas declaradas em blocos/chaves ou identado no Sass, são geralmente as locais e só podem ser acessados dentro do bloco onde foram declarados.

```scss
$var-global: 50px;

.content {
	$var-local: 20px;
	margin-top: $var-global;
	margin-left: $var-local;
}
.sidebar {
	margin-top: $var-global;
	margin-left: $var-local;
	// output: erro, pois var-local não pode ser acessado aqui, fora de seu escopo.
	// margin-left não será compilada na geração do .css
}
```

**shadowing** = variaveis locais podem ter o mesmo nome de variáveis globais. Nesse caso, temos 2 variáveis diferentes com o mesmo nome: uma local e outra global. Isso ajuda a garantir que caso esteja escrevendo uma variável local  não aletere o valor de uma variável global que tenha passado batido.

```scss
$titulo: 'Roboto';

.content {
	$titulo: 'Calibri-Light';
	font-family: $titulo; // acessando o escopo local. output: 'Calibri-Light';
}
.sidebar {
	font-family: $titulo; // acessando o escopo global. output: 'Roboto';
}
```

## regras de estilo

As regras de estilo do CSS sempre começam com **@** e no SASS muitas das features extras vêm na forma de regras básicas que são adicionadas no CSS.

**@use** = carrega módulos: mixins, funções  e variáveis de outros scss e combina css de várias folhas de estilo.

**@forward** = carrega um scss e disponibiliza seus mixins, funções e variáveis quando sua folha de estilo é carregada com **@use**.

**@import** = estende o CSS em regra para carregar estilos, mixins, funções e variáveis de outra folha de estilo.

**@mixin** e **include** = facilitam a reutilização de pedaços de estilos.

**@function** = define funções personalizadas que podem ser usadas em expressões SassScript.

**@extend** = permite que os seletores herdem estilos uns dos outros.

**@at-root** = coloca estilos dentro dele na raiz do documento css.

**@error** = faz a compilação falhar com uma mensagem de erro.

**@warn** = imprime um aviso sem parar totalmente a compilação.

**@debug** = imprime uma mensagem para fins de depuração.

### controles de fluxo e regras simples

regras como **@if**, **@each**, **@for** e **@while** controlam quantas vezes os estilos são emitidos.

o SASS também tem algum comportamento especial para regras simples de CSS: *podem conter interpolação e podem ser aninhadas em regras de estilo*. Alguns como **@media** e **@supports**, também permitem que SassScript seja usado diretamente na própria regra sem interpolação.
