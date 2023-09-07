# Linguagem de Marcação e Estilos - Css

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
            Backgroun-color: blue;
        }
    </style>
    <p>Texto do parágrafo</p>
</div>
```

**Prioridades do CSS**

* **CSS Externo (link externo):** Tem o maior peso e será aplicado a todos os elementos da página, a menos que seja substituído por estilos internos ou em escopo.
* **CSS Interno (dentro do &lt;head&gt;):** Tem um peso intermediário e será aplicado a todos os elementos da página, a menos que seja substituído por estilos em escopo.
* **CSS em Escopo (dentro do &lt;body&gt;):** Tem o menor peso e é aplicado apenas aos elementos dentro do escopo específico em que está definido. Ele será substituído por estilos CSS internos e externos.

Portanto, o &lt;head&gt; manterá a configuração se não for substituído por estilos internos ou em escopo. O peso determina a precedência na aplicação de estilos, com o CSS em escopo sendo o menos prioritário e o CSS externo o mais prioritário. Se houver conflitos entre estilos, o mais prioritário prevalecerá.