# Css3 com SASS / SCSS

Estudo de conceitos e features mais utilizadas para composição de CSS3 ou SASS ou SCSS.
## Introdução à CSS (Cascading Style Sheets)

É uma linguagem de folha de estilo usada para descrever a apresentação de um documento escrito em HTML ou XML (incluindo dialetos XML como SVG, MathML ou XHTML).

O CSS descreve como os elementos devem ser renderizados na tela, no papel, na fala ou em outra mídia.

```css
/* seletores ou grupo de seletores */
header, section, footer { 
    /* 
    * conunto de declarações (propriedade : valor ;) 
    * esses 4 valores são obrigatórios para que não de erro na hora de render
    */
    background-color : black ;
}
```

## Seletores

- **( * )** = seletor universal, ou seja, todo mundo recebe a informação.
- **tipo** = ele referencia a um tipo de elemento/tag. Também é chamado de *seletor impuro*
- **.nome-classe** = com um ponto ele referencia a uma determinada classe instanciada no atributo class de algum/alguns elemento(s) HTML (uma boa prática é usar traço para nomes)
- **#nome-id** = com a hashtag ele referencia a um determinado id instanciado no atributo id de algum elemento HTML
- **[type="tipo-atributo"]** = aqui é especificado algum elemento HTML pelo seu atributo
- **pseudo-seletores** = são palavras reservadas que geralmente referenciam ações ou interações ou eventos na pagina

```css
/* seletor universal */
* { background : red ; }

/* seletor de tipo */
body { background : black ; }

/* seletor de classe */
.fundo-preto { background : black ; }

/* seletor de id */
#nome { background : black ; }

/* seletor por tipo de atributo */
[type="text"] { background : black ; }

/* pseudo seletores */
:hover { background : black ; }
```

## Combinadores de Seletores

- **combinador descendente ( ' ' )** = quando temos espaço entre os seletores. Não importa quantos filhos o seletor pai tem.
- **combinador de filho direto ( > )** = quando temos *>* ente os seletores. Quando os filhos estiverem imediatamente depois do seletor pai.
- **combinador irmão adjacente ( + )** = quem vai receber determinado estilo é um seletor que tem um irmão próximo (depois do +)
- **combinador irmão geral ( ~ )** = quem vai receber determinado estilo é um ou mais seletores que sejam irmão do primeiro seletor antes do sinal 

```css
/* 
* combinador descendente
* abaixo queremos selecionar todos os inputs que descendem de um form
*/
form input { color : blue ; }

/*
* combinador de filho direto (quando é filho direto do pai)
* selecionamos os inputs que estam imediatamente após o form
*/
form > input { color : blue ; }

/*
* combinador irmão adjacente
* indicamos que só receber a cor azul a div que vem logo depois de um form
*/
form + div { color : blue ; }

/*
* combinador irmão geral
* indicamos que só receber a cor azul a ou as div que vem depois de um form
*/
form ~ div { color : blue ; }
```

Quanto mais especifico for a combinação, mais o CSS vai respeitar essa especificidade. Podemos quebrar a especificidade usando uma palavra reservada **!important** depois do valor da propriedade. Essa palavra deve ser usada sempre que não for encontrado o conflito de especificidade.

## Cores

- **nome** = algum nome de cor (white, black, red e etc.) em inglês. Os browsers modernos suportal um total de **140** cores por nome.
- **rgb(RED, GREEN, BLUE)** = referencia a mistura dessas 3 cores variando de 0 a 255 de RED, 0 a 255 de GREEN e 0 a 255 de BLUE. Quanto mais próximo de 0 é um tom mais escuro e quanto mais próximo de 255 é um tom mais claro.

```css
* { 
    color: rgb(255, 255, 255); /* white */
    color: rgb(0, 0, 0); /* black */
    color: rgb(255, 0, 0); /* red */
    color: rgb(0, 255, 0); /* green */
    color: rgb(0, 0, 255); /* blue */
} 
```

- **hexadecimal - #RRGGBB** = variando de 0 até F (0 1 2 3 4 5 6 7 8 9 A B C D E F) podendo ser 00 (ausencia) ou FF (todas as cores). Um detalhe é que sempre que as letras ou caracteres de cada dupla for igual podemos escrever de forma resumida (#RGB).

```css
* { 
    color: #FFFFFF / #FFF; /* white */
    color: #000000 / #000; /* black */
    color: #FF0000 / #F00; /* red */
    color: #00FF00 / #0F0; /* green */
    color: #0000FF / #00F; /* blue */
} 
```

- **HSL (Hue/Matiz, Saturation/Saturação, Lightness/Brilho)** = referencia a mistura de cores variando de 0 a 360 (lembrando um disco de cores) de HUE(Tom da cor), 0 a 100% de Saturation (quanto mais viva) e 0 a 100% de Lightness (brilho da cor).

```css
* { 
    color: hsl(0, 100%, 100%); /* white */
    color: hsl(0, 0%, 0%); /* black */
    color: hsl(0, 100%, 50%); /* red */
    color: hsl(120, 100%, 50%); /* green */
    color: hsl(240, 100%, 50%); /* blue */
} 
```

Ainda relacionado as cores temos a questão da transparência como é chamda **alpha** que varia de 0 a 1 (decimais) onde 0.5 é 50% de transparência ou em hexadecimal de 00 a FF. No rgb teriamos o **rgba(RED, BLUE, GREEN, ALPHA)**, no hexa **#RRGGBBAA** e no hsl teriamos o **hsla(H, S, L, A)**.


## Unidades de medida no CSS

Os comprimentos (length) representam várias unidades diferentes para mostrar comprimento em CSS. São números seguidos por uma unidade de comprimento. Algumas propriedades aceitam números negativos. Nesse universo temos dois tipos de medidas: **Absolutas** e **Relativas**.

As medidas absolutas:

- cm, mm, in (polegadas/inches), px (pixels), pt (pontos/points), pc (paicas)

Um detalhe importante é que dispositivos móveis tem 2 medidas: a medida física e a medida do CSS relativas.

As medidas relativas:

- % (porcentagem), em (tamanho de uma letra M no texto), rem (Root M - M principal da pagina), ch (unidade de caractere), ex (tamanho de uma letra X no texto), vw (largura da janela de exibição/viewport width - ignora barras de rolagem), vh (altura da janela de exibição/viewport height - ignora barras de rolagem), vmin (janela de exibição minima), vmax (janela de exibição maxima), fr (fração restante)

## Box Model (modelo de caixa)

É um dos conceitos mais importantes do CSS3. Todos os elementos HTML podem ser considerados como caixas. No CSS, o termo **modelo de caixa** é usado quando se fala em design e layout. O modelo de caixa é uma caixa que envolve todos os elementos HTML. Consiste em : **margins(margens)**, **bordas**, **paddings(preenchimentos)** e **conteúdo**.

A mais externa é a MARGEM e dentro dela temos a BORDA e dentro dela o PADDING e dentro de tudo isso o CONTEÚDO.

![box model](https://tableless.github.io/iniciantes/assets/img/box-model.png)

```css
/* padrão dos navegadores */
/* o conteúdo que define o tamanho da caixa (antigamente) */
* { box-sizing: content-box; } 

/* hoje usamos o tamanho da caixa por borda */
* { box-sizing: border-box; }

div {
    /* 
    * somando 50 + 2 + 2 + 1 + 1 + 5 + 5 = 66 o tamanho da div no content-box 
    */
    width: 50px;
    height: 10px;
    padding: 2px;
    border-width: 1px;
    margin: 5px;
}
```

O padrão **borde-box** do box-sizing facilita muito, pois o tamanho é mantido, só precisando ser controlado toda parte interna à BORDA.

Importante saber que as direções sempre seguem a ordem TOP, RIGHT, BOTTOM e LEFT.

## Armadilhas CSS3 [IMPORTANTE]

 - cuidado com nome de arquivos css ou com o atributo href da tag link
 - cuidado com a localização dos arquivos css
 - css é caseSensitive, melhor escrever tudo minusculo
 - cuidado com especificidade no CSS
  
## Prática com CSS3 (pulsar)

```html
<button type="button" class="pulse">botão</button>
```

```css
body {
    background-color: #17181C;
    color: #FFF;
    font-family: sans-serif;
}
.pulse {
    background: none;
    color: #FF760C;
    border: 2px solid;
    margin: 50px;
    padding: 15px 40px;
    transition: 0.25s; /* executa efeitos de transição */
}
.pulse:hover, .pulse:focus {
    color: #FFF;
    border-color: #EF8F6E;
    box-shadow: 0 0 0 15px rgba(255, 255, 255, 0);
    animation: pulsar 1s; /* usando a propriedade animation chamamos o 'pulsar' */
}

/* usado para criar animações */
@keyframes pulsar {
    0% {
        box-shadow: 0 0 0 0 #EF8F6E;
    }
}
```

## Introdução ao Position

A propriedade **position** define como o elemento deve ser renderizado/posicionado na página.

Por padrão os elementos são posicionados estaticamente (static) que diz que o espaço seja ocupado apenas por ele mesmo.

Além do static temos **fixed**, **absolute**, **relative**, **sticky**.

**static** = é p único que não é afetado pelas propriedades de deslocamento top, right, bottom e left.

**fixed** = o elemento fica fixo em relação a janela de visualização. Com isso ele não tem sua posição afetada mesmo quando o scroll da pagina for rolado.

**absolute** = fica posicionado em relação ao ancestral posicionado mais próximo. Caso não tenha um elemento ancestral posicionado ele usará o corpo da pagina (documento) como relação. Isso fará com que ele acompanhe o scroll quando for rolado.

**sticky** = o elemento se comporta como relative e fixed em determinados momentos. É posicionado em relação até que encontre uma determinada posição na janela de exibição e passe a se comportar como fixo. Geralmente usado para headers que tem que ficar fixo no topo ao scrollar a pagina.

## FlexBox Layout

Módulo de Caixa Flexível é capaz de organizar os elementos de uma interface de modo unidimensional. É possível organizar os elementos como linha ou coluna e usar recursos para alinhar e distribuir isso.

**flex-direction** = define qual eixo principal: coluna (column) ou linha (row - padrão). Todos os elementos que estam dentro de um que tenha a propriedade display como **flex** vão obedecer a direção definida. Temos ainda row-reverse (o inverso de row) e column-reverse(inverso de column).

## Valores Globais de propriedades

São valores que podem ser usados em todas as propriedades css ao menos que tenha alguma regra específica como exceção.

**initial** = força a reinicialização do valor padrão da propriedade.

**inherit** = atribui a herança explícita para a propriedade aplicada. Caso o elemento pai possua a mesma propriedade com algum valor este será replicado para o elemento em questão.

**unset** = desabilita a propriedade em questão.

**revert** = tem a mesma função do initial, mas é aplicado apenas no browser Safari.

## Introdução ao Grid Layout

É um dos novos recursos do CSS3 aplicado para criar layouts em grade. Permite criação bidimensional, trabalhando linhas e colunas, permitindo inumeras variações.

Assim como o Flexbox ele trabalha com um container que será um wrapper dos elementos internos denominados grid items.

Permite combinações com outras tecnologias. É um layout mais fluido onde temos a liberdade de reproduzir mais livremente de acordo com os conceitos que o Designer produziu, podendo manter a fidelidade dos conceitos.

**display: grid** = o elemento que recebe esse valor é o *Grid Container* e ele pode ser o elemento pai de todos os itens de grade.

Qualquer linha vertical ou horizontal de uma grade que faz as divisões entre linhas e colunas são as **grid lines**.

Cada espaço de uma grade é uma **grid cell**, também conhecido como unidade de grade. Já o espaço entre duas linhas adjacentes, horizontais ou verticais, são as **grid tracks** ou faixa de grade (conjunto de grid cells).

**grid area** = espaço total gerado por 4 grid lines, formando um grupo de celulas.

**gutters** = espaços entre as linhas ou colunas (uma célula e outra) do grid. Fazem uma separação entre os elementos do grid.

# Propriedades do CSS3

Podemos criar atalhos (snippets) para otimizar nosso trabalho na criação de um projeto que seja um tanto extenso ou para uso normal no dia a dia. Para isso no VSCode vamos em File > Preferences > User snippets

OBS: Quando o doctype ele não existe ou está posicionado em lugar errado, acaba sendo ignorado. O browser tenta executar o HTML da melhor forma.

## height, max-height e min-height

**height** = define a altura de elementos sem incluir margin, border e padding. Ela permite herança explícita (inherit) não automáticamente. As **max-height** e **min-height** sobrescrevem height.

**max-height** = define uma altura máxima de um elemento. Se o conteudo for maior, ele irá gerar um overflow.

**min-height** = define uma altura mínima de um elemento. Se o conteúdo for menos, a altura mínima será aplicada, caso contrário, ela será ignorada.

## width, max-width e min-width

**width** = define a largura de elementos sem incluir margin, border e padding. Ela permite herança explícita (inherit) não automáticamente. As **max-width** e **min-width** sobrescrevem width.

- Valores de width em vw ignoram margens definidas e pegam a partir o tamanho da área vísivel.
- Valor **fit-content** o width se ajusta de acordo com o tamanho do conteúdo.
- Valor **max-content** vai ser a máxima largura possível de acordo com o conteúdo.
- Valor **min-content** vai colocar o mínimo de largura possível de acordo com o conteúdo.
- Valor **revert** funciona para o Safari com a mesma função do initial.
- Valor **unset** desabilita o valor;

**max-width** = define uma largura máxima de um elemento. Se o conteudo for maior, ele mudará automaticamente a altura do elemento. Se menor, não tem efeito nenhum.

**min-width** = define uma largura mínima de um elemento. Se o conteúdo for menor, a largura mínima será aplicada, caso contrário, ela será ignorada.

*Quando se coloca width como auto, temos a impressão que ele ocupa 100% da tela, mas isso na verdade é um display block colocado pelo navegador por padrão. Portanto, sempre é importante definir um tamanho para o elemento.*

## margin (top, right, bottom, left)

o valor padrão é **0** e não herda valores.

