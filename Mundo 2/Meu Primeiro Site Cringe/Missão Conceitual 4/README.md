# Linguagem de Marcação e Estilos - Css

## Módulo 1 - Como Funciona a CSS

A CSS, ou Folhas de Estilo em Cascata (*Cascading Style Sheets*), é uma linguagem de estilo que fornece total controle sobre a apresentação de um documento escrito em HTML. Por meio dela, é possível, por exemplo, alterar a forma e o posicionamento dos elementos, as cores, os tipos e tamanhos de fontes e muito mais.

A CSS permite a aplicação seletiva de estilos a elementos em uma página HTML. Isso significa dizer que um ou mais estilos podem ser aplicados em um documento inteiro ou mesmo em apenas parte dele. Além disso, um mesmo tipo de elemento pode ter, ao longo do documento, diferentes estilos.

Como teste alterando a formatação de um parágrafo <p> específico.
```css
#p_teste { /* Parágrafo <p> nomeado como p_teste */
	text-align: center; /* Alinha o texto ao centro */
	background-color: black; /* Define cor de fundo como preto */
	color: orange; /* Define a cor do texto como laranja */
	font-size: 16px;/* Define o tamanho da fonte do texto com 16 pixels */
	font-weight: bold; /* Define a fonte como negrito */
	font-style: italic; /* Define o estilo da fonte como itálico */
/* Quando for definir cor, pode ser utilizado o nome ou o código hexa #0ed145 */
}
```



___

### Seletores:

O seletor de classe é definido a partir da declaração do atributo class em um elemento HTML. Já o seletor de identificação é definido com o atributo id.

**Atenção! Embora um elemento possa ter mais de uma classe, terá somente um identificador.**

**HTML:**

```html
<h1 class="texto_vermelho">Título Principal</h1>
<p id="texto_apresentacao">Texto do parágrafo com atributo de identificação.</p>

<h2>Primeiro Subtítulo</h2>
<p class="texto_descricao texto_vermelho"> Texto do parágrafo com atributo de classe.</p>

<h2>Segundo Subtítulo</h2>
<p class="texto_descricao">Texto do parágrafo com atributo de classe.</p>
```

Abaixo poderá ser observado duas sintaxes que produzirão o mesmo efeito.

Ambos seletores são internos.

**CSS: Sintaxe 1**

```css
<style type="text/css">
#texto_apresentacao{font-size: 12px; /* Seletor de ID é representado por uma "#" */
}

.texto_descricao{font-size: 12px; /* Seletor de class é representado por um "." */
}

.texto_vermelho{color: red;
}
</style>

```

**CSS: Sintaxe 2**

```css
<style type="text/css">
#texto_apresentacao{font-size: 12px; /* Seletor de ID é representado por uma "#" */
}

p.texto_descricao{font-size: 12px; /* Seletor de class é representado por um "." */
}

.texto_vermelho{color: red;
}
</style>

```

**Identificador por ID:**

```css
/* Neste exemplo, estamos definindo um estilo específico para o parágrafo com um ID atribuído como "p_teste". Ele terá um fundo preto e cor da fonte laranja. */
#p_teste { 
	background-color: black;
	color: orange;
}
```

**Identificador por classe:**

```css
/* Neste exemplo, estamos definindo um estilo que se aplica a todos os parágrafos <p> da página que não têm um ID específico atribuído. Esses parágrafos terão fundo preto e cor da fonte verde. */
p {
	background-color: black;
	color: green;
}
```



**Boas Práticas:**

Embora não exista um padrão ou preferência quanto a utilizar o seletor id ou class, é importante frisar novamente que um id deve ser aplicado a apenas um elemento, enquanto a class pode ser aplicada a um ou vários elementos.

Embora o navegador não verifique se um mesmo id foi utilizado em diferentes elementos, tal método pode trazer alguns problemas de estilização e comportamento, uma vez que esse seletor também é bastante usado pelo Javascript. Frente a isso, adote a boa prática de definir identificadores únicos.

**Integrando a CSS à HTML**

Há três formas usuais de aplicar estilos em um documento HTML fazendo uso de CSS: Inline, Interna e Externa. No HTML 5 passou a existir a 4ª forma que é CSS em escopo.

* **CSS Inline** - Essa forma implica em declarar o estilo CSS diretamente na tag, no código HTML.

```html
<p style="background-color: blue;">Textp Parágrafo</p>
```

* **CSS Interna** - Também chamada de CSS incorporada, é declarada na seção < head > do documento HTML.

```html
<html>
    <head>
        <style type="text/css">
            p{
                background-color: blue;
            }
        </style>
    </head>
</html>
```

* **CSS Externa** - Nesse caso, os estilos são declarados em um arquivo externo, com extensão “.css” e vinculados ao documento HTML por meio da tag < link > ou da diretiva `@import` dentro da tag `< head >`.

```html
<!-- Via link dentro da tag <head> -->
<html>
    <head>
        <link rel="stylesheet" type="text/css" href="estilos.css" /> 
    </head>
</html>
```

```html
<!-- Via link diretiva @import <head> -->
<html>
    <head>
        <style type="text/css">
           @import url("estilos.css");
        </style>
    </head>
</html>
```

* **CSS em Escopo** - Por meio dela, é possível aplicar estilos no âmbito de escopo, ou seja, específicos para as seções da página em que foram declarados, incluindo os seus elementos filhos. No código abaixo, a tag `< p >` receberá os estilos definidos, sendo a mesma regra válida para outros estilos e elementos que, porventura, venham a fazer parte da `< div >`.

```css
<div>
    <style type="text/css">
        /* Estes estilos serão aplicados apenas dentro da DIV */
        p{
            Background-color: blue;
        }
    </style>
    <p>Texto do parágrafo</p>
</div>
```

**Prioridades do CSS**

O CSS segue um sistema de prioridades que determina a precedência dos estilos. Isso é crucial quando se trata de resolver conflitos de estilos em uma página da web. Aqui está a ordem de prioridade:

1. **CSS Externo (link externo):** Este tipo de estilo tem o maior peso e será aplicado a todos os elementos da página, a menos que seja substituído por estilos internos ou em escopo.
2. **CSS Interno (dentro do `<head>`):** Os estilos internos têm uma prioridade intermediária e também serão aplicados a todos os elementos da página, a menos que sejam substituídos por estilos em escopo.
3. **CSS em Escopo (dentro do `<body>`):** Este tipo de estilo tem a menor prioridade e é aplicado apenas aos elementos dentro do escopo específico em que está definido. Ele será substituído por estilos CSS internos e externos.

Portanto, o `<head>` manterá a configuração se não for substituído por estilos internos ou em escopo. O peso determina a precedência na aplicação de estilos, com o CSS em escopo sendo o menos prioritário e o CSS externo o mais prioritário. Se houver conflitos entre estilos, o mais prioritário prevalecerá.

**Herança e especificidade**

* **Herança** - A CSS permite que a aplicação de propriedades a elementos pais seja herdada pelos seus elementos filhos. Essa capacidade de herdar estilos é chamada de `Efeito Cascata`. Vale ressaltar que nem todas a propriedades CSS podem ser herdadas pelos filhos.

```html
<style>
div{
    color: blue;    
}
</style>

<div>
    Texto solto na Div - Exemplo 1
    <p>Texto do parágrafo que é filho da Div</p>

    <!-- O resultado do fragmento de código mostrará tanto o texto solto quanto o 			texto dentro da tag <p> com a cor azul. Isso significa que
    a tag <p>; herdou o estilo definido para o seu pai, a tag <div>. -->			
</div>
```

* **Especificidade** - Agora, há um estilo específico definido para todas as tags  `< p >` que sejam filhas de tags `< div >`. Com isso, ao visualizarmos o resultado no navegador, teremos o texto solto na cor azul e o texto dentro da tag na cor vermelha.

```html
<style>
        div{
        color: blue;    
    }
    #ex2 > p {
        color: red;
    }
</style>

<div id="ex2">
    Texto solto na Div - Exemplo 2
    <p>Texto do parágrafo que é filho da Div</p>
    <p>Segundo parágrafo exemplo 2</p>

    <!-- O resultado do fragmento de código mostrará tanto o texto solto quanto o texto 	dentro da tag <p> com a cor azul. Isso significa que a tag <p> herdou o estilo 			definido para o seu pai, a tag <div>;.-->
</div>
```

## Módulo 2 - Recursos de cores

Com a utilização de CSS, podemos manipular as cores de elementos HTML, seja na aparência das caixas seja na cor de texto. Para isso, há uma série de propriedades CSS disponíveis para diversos elementos, mas antes vamos abordar as formas de definição de cores.

As cores em CSS podem ser escritas de três modos:

1. Com palavras-chave, nas quais podem ser usados os nomes das cores (seguindo as definidas pela especificação CSS) ou a notação hexadecimal. Por exemplo: blue, red, #FFFFFF etc.
2. Com um sistema de coordenada cúbica RGB, com as notações rgb() e rgba().
3. Com um sistema de coordena cilíndrica HSL, com as notações hsl() e hsla().

* **Propriedades de cor**

Essas propriedades se referem a quais elementos podemos definir cores.

Veja na tabela a seguir as principais propriedades relacionadas à cor, bem como os elementos aos quais podem ser aplicadas.

| Propriedade        | Serve para definir         | Onde pode ser utilizada                                      |
| ------------------ | -------------------------- | ------------------------------------------------------------ |
| `color`            | Cor de Textos              | Elementos que contenham texto, como `<h1>... <h6>`, `<p>`, `<header>`, `<section>`, etc. |
| `background-color` | Cor de fundo dos elementos | Aplica-se a qualquer elemento HTML                           |
| `border-color`     | Cor da borda               | Aplica-se a qualquer elemento HTML                           |
| `outline-color`    | Cor da borda externa       | Aplica-se a qualquer elemento HTML                           |

Como modelo de Seletor de Cores pode ser utilizado o modelo disponível na [W3C](https://www.w3schools.com/colors/colors_picker.asp). Ou até mesmo a ferramenta de Input Color no HTML5.
```html
<h3>Input color</h3>
    <label for="favcolor">Selecione a cor desejada:</label>
    <input type="color" id="favcolor" name="favocolor" value="#ff0000"><br />
```

* **Texto**

A estilização de textos com o uso de CSS é dividida em duas partes.

Em linhas gerais, os navegadores aplicam estilos padrões quando renderizam conteúdos textuais. Veja a seguir algumas propriedades CSS que alteram esse comportamento padrão.

Os navegadores aplicam os estilos padrões quando renderizam conteúdos textuais.

| Layout do texto                                              | Estilos das fontes                          |
| :----------------------------------------------------------- | ------------------------------------------- |
| Espaçamento entre os caracteres e linhas;<br />alinhamento em relação ao *container*. | Família, tamanho, efeitos como negrito etc. |

* **Alinhamento de texto**

Para alinhar o texto em razão ao container inserido deve-se utilizar `<text-align>` a ser definido em quatro valores `left, right, center, justify` .

```css
text-align: left;
text-align: right;
text-align: center;
text-align: justify;
```

* **Espaçamento entre linhas**

A propriedade `line-height` permite alterar o espaçamento vertical entre as linhas de texto. Seus valores possíveis são:

1. Normal: Valor padrão do navegador (entre 1 e 1.2 em relação ao font-size, dependendo do navegador).
2. Número: Valor inteiro ou decimal que será multiplicado ao tamanho da fonte.
3. Comprimento: Valor unidades como pixels, pontos, “em” etc.

A maneira mais recomendada para declarar o espaçamento entre linhas é utilizando o valor em número.
Desse modo, o espaçamento será o resultado da multiplicação do valor definido pelo tamanho da fonte. Neste exemplo: 1.5 * 14px = 21.

```css
style="line-height: 1.5; font-size: 14px"
```

* **Espaçamento entre letras e palavras**

As propriedades `letter-spacing` e `word-spacing` permitem alterar o espaçamento entre letras e/ou palavras respectivamente. Podem assumir valores de comprimento – “px”, “pt” etc.

```css
style="letter-spacing: 1px; word-spacing: 5px"
```

* **Fontes**

Em relação às fontes, há propriedades CSS para definir família, tamanho, estilo, entre outras possibilidades. 

1. **Font-Family (Família da Fonte):** Essa propriedade permite escolher a família de fonte que será usada em um elemento da página. Você pode listar várias fontes em ordem de preferência, caso a primeira não esteja disponível no dispositivo do usuário. Por exemplo, "Arial, Helvetica, sans-serif" indica que o navegador deve usar Arial se disponível, caso contrário, Helvetica e, se nenhum deles estiver disponível, uma fonte sans-serif genérica.
2. **Font-Size (Tamanho da Fonte):** Essa propriedade define o tamanho do texto em um elemento. Você pode usar diferentes unidades de medida, como pixels, porcentagem ou em para especificar o tamanho. Por exemplo, "16px" define um tamanho de fonte de 16 pixels.
3. **Font-Style (Estilo da Fonte):** Esta propriedade é usada para aplicar estilo itálico ao texto. Ela tem três valores principais: "normal" (sem estilo), "italic" (texto inclinado) e "oblique" (texto inclinado de forma mais acentuada).
4. **Font-Weight (Peso da Fonte):** A propriedade font-weight define a espessura do texto, incluindo valores como "normal" (padrão), "bold" (negrito), "lighter" (mais leve) e "bolder" (mais ousado). Você também pode usar valores numéricos para um controle mais preciso, variando de 100 (muito fino) a 900 (muito negrito).

* **Web Fontes**

As Web Fontes são um recurso importante em tipografia. Antes, a estilização de texto estava limitada às fontes disponíveis nos sistemas operacionais dos usuários. No entanto, com a introdução da regra `@font-face`, tornou-se possível usar Web Fontes. Essa propriedade permite a utilização de fontes que são baixadas pelo navegador quando a página é carregada. Isso oferece maior controle sobre o layout de uma página em relação às fontes, além da capacidade de usar fontes com designs visuais mais elaborados.

* **Utilizando a regra `@font-face`**

A regra `@font-face` do CSS permite que você incorpore fontes personalizadas em seu site, úteis quando você deseja usar uma fonte que não está disponível nos sistemas dos usuários. Aqui está uma explicação detalhada de como usar a regra `@font-face`:

**`@font-face`**: Esta regra é usada para definir uma fonte personalizada.

**`font-family`**: Aqui, você nomeia a família da fonte que está importando, que será usada em seu CSS para aplicar a fonte aos elementos.

**`src`**: Esta propriedade define onde o navegador deve procurar a fonte. Você pode especificar várias fontes aqui, e o navegador usará a primeira disponível. No exemplo abaixo, primeiro tenta carregar uma fonte local chamada ‘Minha Fonte Local’. Se essa fonte não estiver disponível, tenta ‘Outra Fonte Local’. Se nenhuma fonte local estiver disponível, ele carregará a fonte da web no formato WOFF do caminho especificado.

**`format`**: Esta propriedade especifica o formato da fonte da web. O formato mais comum é WOFF, mas existem outros, como TTF e EOT.

**Observação**: Ao definir uma `@font-face` em seu código, ela será a primeira na lista de fontes definidas. Se o navegador não puder carregar a fonte por algum motivo, passará para a próxima da lista, que também pode ser definida por `font-face` ou `fonte-local`.

```css
/* Exemplo de como usar a regra @font-face em seu CSS: */
@font-face {
  font-family: 'MinhaFontePersonalizada'; /* Nomeie sua fonte */
  src: local('Minha Fonte Local'), /* Tente esta fonte local primeiro */
       local('Outra Fonte Local'), /* Se a primeira não estiver disponível, tente esta */
       url('caminho-da-sua-fonte.woff') format('woff'); /* Se nenhuma fonte local estiver disponível, carregue esta fonte da web */
}
```

## Módulo 3 - Conceitos de box model

