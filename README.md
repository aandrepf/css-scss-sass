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

## margin (top, right, bottom, left) e padding(top, right, bottom, left)

o valor padrão é **0** e não herda valores.

**margin** = define a distancia externa da borda do elemento adicionando espaço extra.

**padding** = define a distância entre a borda e o conteúdo do elemento.

Quando está definico o box-sizing como *content-box*, com o padding temos um **side-effect**, ou efeito colateral, onde ao adicionar padding ele soma ao tamanho original do bloco pai. Com o valor *border-box* corrigimos isso, pois está dizendo que queremos que o tamanho seja referente a uma borda e outra.

## border (top, right, bottom e left)

Border aceita valores de cor | transparent | initial | inherit. O default é a cor atual do elemento e não herda valores de outros elementos.

**border-color ([border-top-color, border-right-color, border-bottom-color, border-left-color])** = define a cor da borda.

**border-style ([border-top-style, border-right-style, border-bottom-style, border-left-style])** = define o estilo da linha da borda. Aceita valores [none (default), hidden, dotted, dashed, solid, double, groove, ridge, inset, outset, initial, inherit].

**border-width ([border-top-width, border-right-width, border-bottom-width, border-left-width])** = define a largura da borda. Aceita valores [medium (default), thin, thick, tamanho, initial, inherit]

**border-radius ([border-top-left-radius, border-top-right-radius, border-bottom-right-radius, border-bottom-left-radius])** = define os cantos arredondados da borda. esse aceita valor resumido para os 4 lados ou border-radius-collapse que pega os lados opostos. Com valor 50% par aos 4 lados, ele cria um círculo.

```html
<style>
    * { box-sizing: border-box; }
    body {
        margin:0; 
        padding: 0;
        display: flex; 
        justify-content: center; 
        align-items: center; 
        background-color: #c33;
        height: 100vh;
    }
    .heart {
        position: relative;
        width: 100px;
        height: 90px;
    }
    .heart:after, .heart:before {
        content: '';
        position: absolute;
        top:0;
        left: 50px;
        width: 45px;
        height: 80px;
        background-color: #fff;
        border-radius: 50px 50px 0 0;
        transform: rotate(-45deg);
        transform-origin: 0 100%;
    }
    .heart:after {
        left: 0px;
        transform: rotate(45deg);
        transform-origin: 100% 100%;
    }
    div#bph2018style { display: none; }
</style>


<body>
    <div class="heart"></div>
</body>
```

## boder-image (source, width, slice, outset, repeat)

Essas propriedades dependem do border-width ser de pelo menos 1px de tamanho.

**source [none | src da imagem | initial | inherit]** = define a origem da imagem que deseja usar em torno do elemento. Valor padrão *none*;

**width [number | percent (%) | auto | initial | inherit]** = define a largura da borda que tem uma imagem. Valor padrão *1*;

**slice[number | % | fill | initial | inherit]** = define como a imagem da borda será dividida. Valor padrão *100%*;

**outset[number | initial | inherit]** = define a distancia entre o elemento e sua borda com uma imagem. Valor padrão *0*;

**repeat[stretch/esticar | repeat | round | space | initial | inherit]** = define se a imagem da borda será repetida para contornar todo elemento ou se deve ser esticada para envolver todo elemento. Valor padrão *strecht*;

o border-image com todas as propriedade resumidas, segue a ordem abaixo; Os valores em ordem devem ser escritos assim:

```css
seletor {
    border-image: source slice / width / outset repeat; /* deve conter essa barra, pois senão pode quebrar o funcionamento */
}
```

## boder-collapse [collapse | separate (default) | unset | initial | inherit]

Define se as bordas de uma tabela devem ser mescladas em uma unica, ou se devem se manter separadas.

## border-spacing [length (default: '2px') | inherit | initial | unset]

Define a distancia que haverá entre as bordas de uma tabela. Essa é uma das poucas propriedades que herdam implícitamente, ou seja, se definida na table, todos os internos recebem o valor;


## box-sizing [content-box (default) | border-box | initial | inherit]

Define como a largura e altura de um elemento são calculados. Se irão incluir o padding e bordas ou não.

## overflow [overflow-x, overflow-y] [visible | hidden | scroll | auto (default) | inherit | initial | unset]

Define o comportamento do conteúdo quando este estoura os limites definidos de altura e largura da caixa. Se não for definido o valor de y, o vor de x será copiado para y;

```css
overflow: overflow-x overflow-y /* Valores possíveis para x e y: visible (default) | hidden | scroll | auto | initial | inherit */
```

## overflow-wrap [normal (default) | break-word | anywhere (valor recente) | initial | inherit | unset]

Aplicado para elementos em linha, adicionando uma quebra de linha sempre que uma palavra for gerar um estouro na caixa.

## overflow-block e overflow-inline [visible | hidden | scroll | auto (default) | inherit | initial | unset]

O overflow-block determina o que deve acontecer com o conteúdo de um elemento de bloco quando este estoura os limites do bloco. Pode direcionar para overflow-y ou overflow-x dependendo do modo de escrita do documento. Esta propriedade está disponível somente no **Firefox**. Em sistemas muito antigos ainda pode ser encontrado essa propriedade que, hoje em dia é substituível pelo **overflow**.

Já o overflow-inline especifica o que deve ser exibido quando o conteúdo estoura os limites de um elemento de linha onde foi definida e pode ser usada na condição de uma media query. Pode direcionar para overflow-y ou overflow-x dependendo do modo de escrita do documento. Esta propriedade está disponível somente no **Firefox**.

## resize [none (default) | both | horizontal | vertical | block (por enquanto só Firefox) | inline  (por enquanto só Firefox) | inherit | initial | unset]

Determina se e como um elemento HTML poderá ser redimensionado ou não pelo usuário.

## z-index [auto (deafault) | number | initial | inherit | unset]

Determina a ordem da pilha de um elemento. O elemento com maior ordem está sempre na frente de um elemento com uma ordem menor. Essa propriedade depende de um position, mas que não seja *static*.

## outline [outline-style, outline-color, outline-width, outline-offset]

A linha do outline ela não faz parte do box-model estando do lado de fora da caixa, onde ele termina na borda. Tem a finalidade de destacar o elemento.

**outline-style** = define o estilo da linha de contorno do elemento. Valores [auto | dashed | dotted | double | groove | hidden | inherit | initial | none (default) | outset | revert (initial, mas para o Safari) | ridge | solid | unset]

**outline-color** = define a cor da linha de contorno do elemento. Valores [ivert (default, só no IE8) | color (default se a cor do texto for definida) | initial | inherit | unset]

**outline-width** = define a largura da linha de contorno externa do elemento. Valores [medium (default) | thin | thick | length | initial | inherit | unset]

**outline-offset** = define a distancia da linha de contorno externa com a borda do elemento. Valores [length (0 é o default) | initial | inherit | unset]

```css
div {
    outline: 10px solid red; /* abreviado de outline-width outline-style outline-color */
    outline-offset: 20px; /* não entra na abreviação */
}
```

## display

O seu valor padrão depende muito do tipo de elemento.

lista de Valores: [ínline, block, inline-block, contents, flex, inline-flex, grid, inline-grid, list-item, run-in, none, table, inline-table, table-caption, table-column-group, table-header-group, table-footer-group, table-cell, table-column, table-row, initial, inherit, unset].

a diferença entre **inline** e **inline-block** é que não da pra mexer nas dimensões do elemento que está como inline.

o **contents** é indicado quando o conteúdo do elemento precisa existir independente da forma de apresentação.

alguns displays como **list-item** e **table** e seus adjacentes funcionam para criar estruturas de listas e tabelas respectivamente, mas deve-se atentar quanto ao SEO, pois a tag própria para esses tipos de estruturas são mais relevantes para os motores de busca do que elementos com esses tipos de display.

## cursor (ponteiro do mouse)

Define como o cursor do mouse ira aparecer quando passamos o mouse por um determinado elemento. valores [auto | default (default) | cursor-type | valores globais].

Para o **cursor-type** temos alguns valores pré-definidos de acordo com esse link sobre [cursores](https://developer.mozilla.org/pt-BR/docs/Web/CSS/cursor).

## background

**background-color** = define a cor de fundo de um elemento. [color | transparent (default) | valores globais]

**background-image** = define uma imagem de fundo de um elemento. [url | none (default) | valores globais]. [lorem picsum](https://picsum.photos/).

**background-size** = define o tamanho da imagem de fundo. [auto (default) | length | cover (tenta cobrir a maior area disponível mesmo que perca partes da imagem) | contain (tenta cobrir a maior area disponível, mas sem que perca partes da imagem) | valores globais]

**background-repeat** = define como a imagem de fundo será repetida. [repeat (default) | repeat-x | repeat-y | no-repeat | valores globais]


```css
div {
    background-size: 100% auto | 100%; /* largura: 100% altura: auto | largura e altura: 100% */
}
```

**background-position** = define a posição inicial de uma imagem de fundo. [top | right | bottom | left | center | length | x% y% (default: 0% 0%) | valores globais]

**background-attachment** = define se uma imagem de fundo será rolada com o restante da pagina ou não. [scroll (default) | fixed | local | valores globais]


# FlexBox Layout

Módulo de Caixa Flexível é capaz de organizar os elementos de uma interface de modo unidimensional. É possível organizar os elementos como linha ou coluna e usar recursos para alinhar e distribuir isso.

Algumas propriedades do flexbox vão no container e outras vão nos itens dentro desse container (flex-items);

## Propriedades de Container (flex-container)

**flex-direction** = define qual eixo principal: coluna (column) ou linha (row - padrão). Todos os elementos que estam dentro de um que tenha a propriedade display como **flex** vão obedecer a direção definida. Temos ainda row-reverse (o inverso de row) e column-reverse(inverso de column). Valores [row (default) | row-reverse | column | column-reverse | initial | inherit | unset]

**flex-wrap** = define se os itemns flexiveis devem ou não quebrar. Valores [nowrap (default) | wrap | wrap-reverse | initial | inherit | unset]

**flex-flow** = define o fluxo dos itens flexíveis. Valores [flex-direction flex-wrap(default: row nowrap) | initial | inherit | unset]

```css
.container {
    flex-flow: row nowrap; /* abreviado de [flex-direction flex-wrap] */
}
```

**justify-content** = define o alinhamento dos itens flexiveis no eixo principal. [flex-start (default) | flex-end | center | space-between | space-around | space-evenly | initial | inherit | unset]. Os valores space-between, space-around e space-evenly são exclusivos de justify-content. Ela está sempre associada com a propriedade *flex-direaction* que define o eixo principal.

**align-items** = define o alinhamento dos elementos filhos no eixo secundário (se é row, o secundario é o eixo vertical, se é column o eixo secundário é o horizontal). È o equivalente a denfinir **align-self** em cada um dos elementos. [normal (default) | stretch | center | start (gridlayout) | end (gridlayout) | flex-start | flex-end | self-start | self-end | baseline | first baseline | last baseline | safe center | unsafe center | global values]

*Obs.: um elemento filho pode possuir a propriedade **align-self** para substituir o alinhamento definido no container.*

O valor stretch só funciona caso os items não tenham width (caso o eixo secundario seja o horizontal) definido ou height (caso o eixo secundário seja o vertical), pois ele estica os items atá a largura ou altura máxima do container.

**align-content** = define o comportamento da propriedade flex-wrap. É semelhante a align-items, porém alinha as linhas flexíeis. [normal | stretch (default) | center | start (gridlayout) | end (gridlayout) | flex-start | flex-end | self-start | self-end | baseline | first baseline | last baseline | space-between | space-around | space-evenly | safe center | unsafe center | global values].

Align-content só faz sentido se usarmos junto com flex-wrap.

**place-content** = abreviação de duas propriedades: align-content justify-content. Se o segundo valor náo for informado, o valor do primeiro servirá para ambos.

```css
.container {
    place-content: center center / center; /* align-content: center justify-content: center */
}
```

## Propriedades de Items de Container (flex-items)

**justify-items** = é usada em containers com display grid e alinham os items de suas áreas de grade no eixo embutido. Equivale a justify-self (dos itens). [legacy | auto | normal (default) | stretch | center | start | end | flex-end | flex-start | self-start | self-end | left | right | baseline | first baseline | last baseline | safe center | unsafe center |legacy right | legacy left | legaci center | valores globais]

**place-items** = abreviação das propriedades: align-items justify-items. Se o segundo valor náo for informado, o valor do primeiro servirá para ambos.

```css
.container {
    place-items: center center / center; /* align-items: center justify-items: center */
}
```

**justify-self** = define o alinhamento do item no eixo primário dentro do container flex. Valores [auto (default) | normal | first | last | start | end | stretch | center | flex-start | flex-end | self-start | self-end | left | right | baseline | first baseline | last baseline | valores globais]

**flex-grow (esticar flex-items)** = define como o flex-item deve crescer. Valores [number (default: 0) | valores globais].

Como o padrão é 0 os flex-itens ocupam um tamanho máximo relacionado ao conteúdo interno deles ou a um width definido. Ao colocar 1 eles tentarão ter a mesma largura e vão ocupar 100% do flex-container. A propriedade **justify-content** não funciona quando temos flex-grow definido.

**flex-basis (tamanho minimo dos flex-item)** = define o tamanho inical do flex-item antes da distribuição do espaço restante. Valores [auto (default) | length | number | fill | max-content | min-content | fill-content | content | valores globais]

Quando temos flex-grow igual a 1 e o basis está como *auto* o restante para ocupar o container é distribuído ao redor do conteúdo do flex-item.

**flex-shrink (comprimir flex-items)** = define como o flex-item será reduzido em relação ao restante dos itens do mesmo container-flex. Valores [number (default: 1) | valores globais]

**flex** = define o comprimento dos flex-itens. É a abreviação das propriedades: flex-grow flex-shrink flex-basis. Valores [flex-grow flex-shrink flex-basis (default) | auto | valores globais]

```css
.container > div {
    flex: 0 1 auto; /* flex-grow: 0 flex-shrink: 1 flex-basis: auto */
}
```

**order** = define a ordem de um flex-item em relação aos outros flex-itens do container. valores [number (default: 0) | valores globais]

**align-self** = define o alinhamento de um item que está no eixo secundário dentro do flex-container. valores [auto (default) | stretch | center | flex-start | flex-end | baseline | valores globais]

**place-self** = abreviação das propriedades: align-self justify-self. Se o segundo valor náo for informado, o valor do primeiro servirá para ambos.

```css
.container {
    place-self: center center / center; /* align-self: center justify-self: center */
}
```