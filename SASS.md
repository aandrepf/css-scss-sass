# Pré-processador de CSS

| Sass | https://sass-lang.com |
| Sass Install | https://sass-lang.com/install |
| Sass Guide | https://sass-lang.com/guide |
| Sass Doc | https://sass-lang.com/documentation |

| Pravatar | https://pravatar.cc/ |

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

