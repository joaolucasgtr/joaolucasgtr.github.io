---
title: O que é Markdown?
date: 2015-03-04 11:52:32
tags: markdown
categories: fundamentals
thumb: markdown.svg
---

**Markdown** é uma [linguagem de marcação leve](https://en.wikipedia.org/wiki/Lightweight_markup_language) com sintaxe de texto puro. Seu *design* permite que seja convertida para muitos formatos, incluindo `.html`, `.pdf`, `.docx`, entre outros.

O propósito principal por trás do **Markdown** é fazer com que o texto seja o mais limpo e legível possível, não contendo *tags* ou instruções de formatação, ou seja, com **Markdown** você escreve tendo o foco principal no conteúdo e não em código.

Embora criado há bastante tempo, em 2004, o **Markdown** é uma prova de futuro (**Future proof**), pois simplesmente representa texto simples, ao contrário de outras maneiras de escrita [*WYSIWYG*](https://en.wikipedia.org/wiki/WYSIWYG).

Sendo simplesmente texto, você está livre para usar qualquer editor simples para utilizá-lo, diferentemente do *Microsoft Word*, por exemplo, que possui mais de 10 tipos diferentes de extensão para escrita.

## Por que utilizar?

Devido a sua simplicidade de escrita e interpretação, sua adoção foi massiva e tornou-se uma espécie de padrão, não oficial, para escrita de documentações e aplicativos de chat.

O [**Github**](https://github.com/) utiliza o **Markdown** com alguns recursos extras em seu site para simplificar a escrita de **Issues** ou arquivos **README**; [**Trello**](https://trello.com/) na escrita de seus populares **cards**; [**Slack**](https://slack.com/) para formatação de mensagens; além de diversas ferramentas para geração de sites estáticos que adotaram a escrita em **Markdown** como padrão de publicação de conteúdo.

A propósito, todo o conteúdo deste blog é escrito utlizando **Markdown**. =)

## Referências

- [Daring Fireball](https://daringfireball.net/projects/markdown/), by John Gruber;
- [Github Flavored Markdown](https://github.github.com/gfm/)
- [Markdown on Wikipedia](https://en.wikipedia.org/wiki/Markdown)

## Exemplos

A seguir, alguns exemplos básicos para demonstração da marcação:

- **Títulos:**

```md
# h1 Heading
## h2 Heading
### h3 Heading
#### h4 Heading
##### h5 Heading
###### h6 Heading
```

# h1 Heading
## h2 Heading
### h3 Heading
#### h4 Heading
##### h5 Heading
###### h6 Heading

- **Ênfase:**

```md
**Este texto está em negrito**

__Este texto está em negrito__

*Este texto está em itálico*

_Este texto está em itálico_

~~RASURADO~~
```

**Este texto está em negrito**

__Este texto está em negrito__

*Este texto está em itálico*

_Este texto está em itálico_

~~RASURADO~~

- **Blockquotes:**

```md
> Blockquotes também podem ser aninhados...
>> ...utilizando outro sinal de **maior que**...
> > > ...ou com espaço entre os sinais.
```

> Blockquotes também podem ser aninhados...
>> ...utilizando outro sinal de **maior que**...
> > > ...ou com espaço entre os sinais.

- **Listas:**

Não ordenadas:

```md
+ Crie listas iniciando a linha com `+`, `-`, or `*`
+ Sub-listas são feitas indentando por 2 espaços:
  - Alterar o caractere de marcação força a criação de nova lista:
    * Ac tristique libero volutpat at
    + Facilisis in pretium nisl aliquet
    - Nulla volutpat aliquam velit
+ Simples!
```

+ Crie listas iniciando a linha com `+`, `-`, or `*`
+ Sub-listas são feitas indentando por 2 espaços:
  - Alterar o caractere de marcação força a criação de nova lista:
    * Ac tristique libero volutpat at
    + Facilisis in pretium nisl aliquet
    - Nulla volutpat aliquam velit
+ Simples!

Ordenadas:

```md
1. Lorem ipsum dolor sit amet
2. Consectetur adipiscing elit
3. Integer molestie lorem at massa

4. Você pode usar números sequenciais...
5. ...ou manter todos os números como `1.`
```

1. Lorem ipsum dolor sit amet
2. Consectetur adipiscing elit
3. Integer molestie lorem at massa

4. Você pode usar números sequenciais...
5. ...ou manter todos os números como `1.`


- **Código:**

```md
Código em `linha`
```
Código em `linha`


```md
Código indentado:

    // comentários...
    linha 1 de código
    linha 2 de código
    linha 3 de código
```

Código indentado:

    // comentários...
    linha 1 de código
    linha 2 de código
    linha 3 de código

- **Links:**

```md
[link com texto](http://joaolucasgtr.gitlab.io/)
```

[link com texto](http://joaolucasgtr.gitlab.io/)

```md
[link com título](http://joaolucasgtr.gitlab.io/ "texto do título!")
```

[link com título](http://joaolucasgtr.gitlab.io/ "texto do título!")


- **Imagens:**

```md
![Minion](https://octodex.github.com/images/minion.png)
![Stormtroopocat](https://octodex.github.com/images/stormtroopocat.jpg "The Stormtroopocat")
```

![Minion](https://octodex.github.com/images/minion.png)
![Stormtroopocat](https://octodex.github.com/images/stormtroopocat.jpg "The Stormtroopocat")

...para a especificação completa de recursos, visite os links referenciados.
