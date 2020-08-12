---
title: O princípio KISS
tags: kiss
categories: engineering
thumb: gears.svg
date: 2017-01-08 12:08:33
---

A sigla **KISS** é o acrônimo para **“keep it simple, stupid“** ou **“keep it stupid simple“**. Este princípio visa reduzir casos de **Over Engineering**, ou excesso de engenharia, tendo foco principal na simplicidade, evitando ao máximo toda complexidade desnecessária. 

Código simples é menos passível de *bugs*, mais fácil de se ler, compreender e aplicar manutenções futuras (até mesmo para você que escreveu a primeira versão). 

Embora seja amplamente discutida a sua aplicação na área de desenvolvimento de *software*, a criação do **KISS** não possui relação direta com a programação, sendo simplesmente a sintetização de um conceito muito mais antigo sobre minimalismo. 

Citações que representam o princípio:

> “Simplicity is the ultimate sophistication.”  — Leonardo da Vinci
> (Simplicidade é a sofisticação suprema)

> “Less is more.” — Mies Van Der Rohe's 
> (Menos é mais) 

> "It seems that perfection is reached not when there is nothing left to add, but when there is nothing left to take away" — Antoine de Saint Exupéry's
> (A perfeição é alcançada não quando não há mais nada a acrescentar, mas quando não há mais nada a se tirar)

**Porém, manter as coisas simples, ironicamente, não é simples!**

Para aplicar o **KISS** é preciso pensar de forma abstrata, requer conhecimento e domínio sobre o que você trabalha (linguagem, framework, biblioteca, etc...), autocrítica, paciência, empatia, entre outros.

## Autocrítica

Se você já possui experiência de mercado na área, lidando diariamente com bases de código, é bem provável que você irá perceber que, infelizmente, uma pequena fração desse montante pode ser considerada código simples. Alguns fragmentos podem ser considerados até “anti-padrões”. Eis a questão, o mesmo serve para o seu código, que pode ser perfeitamente compreensível agora, porém experimente visitá-lo após alguns meses...

A causa para tanta escrita de código complexo pode não ser somente a falta de habilidades técnicas, mas também pode ser ocasionada por desenvolvedores que gostam de se “exibir”, escrevendo códigos muito complexos para parecem mais inteligentes.

Outra citação importante:

> "Any fool can write code that a computer can understand. Good programmers write code that humans can understand." — Martin Fowler
> (Qualquer tolo consegue escrever código que um computador entenda. Bons programadores escrevem código que humanos possam entender)

Se você acha que já escreve códigos simples, aí vai uma dica: sempre há espaço para melhorar.

## Mas por que eu deveria aplicar o KISS?

Sua aplicação irá te beneficiar das seguintes maneiras: 

- Você irá resolver mais problemas, mais rapidamente;
- Você irá produzir código para resolver problemas complexos com menos linhas de código;
- Você irá aumentar a qualidade do código que produz;
- Será mais fácil construir sistemas grandes, com manutenção facilitada;
- Sua base de código será mais flexível, mais fácil de estender, modificar ou refatorar quando novos requisitos chegarem;
- Você poderá trabalhar em grandes grupos de desenvolvimento e grandes projetos, pois todo o código é estupidamente simples.

## Como aplicar

Uma tática simples para aplicação do princípio é sempre quebrar grandes problemas em problemas menores, mais simples e mais compreensíveis. Ao não aplicar este conceito, a tendência é que sejam escritos códigos espaguete, onde existirão muitas condicionais, desvios de fluxo, má estruturação, grande número de variáveis, etc. 

Esse conjunto poderá acabar gerando classes de quinhentas a mil linhas (*ou mais*) e vários métodos com dezenas e mais dezenas de linhas de código. Claramente violando o princípio **KISS**.

Outras maneiras práticas de aplicação podem ser:

- **Seja humilde e não se considere um gênio**, este é seu primeiro erro. Pense que você não precisará ser pois irá escrever códigos tão simples que ninguém precisará ser um gênio para entender;
- **Quebre grandes problemas em pequenos:** cada problema deve ser facilmente resolvido com uma ou duas classes;
- **Mantenha métodos pequenos:** limitando apenas uma responsabilidade por método facilitará a escrita de métodos pequenos, até vinte linhas é o cenário ideal. Isto não só irá aprimorar a leitura como também será **muito** mais fácil encontrar *bugs*;
- **Mantenha poucas condicionais:** quantidades grandes de condicionais em um método podem ser um sintoma de que seu problema ainda não foi quebrado o suficiente;
- **Resolva o problema, então codifique:** organizar mentalmente, ou em um rascunho, como resolver um problema irá facilitar o processo de escrita, pois será apenas uma tarefa mecânica de traduzir em código o que você já planejou anteriormente;
- **Não tenha medo de jogar código fora:** refatoração é uma prática importante no processo de crescimento e amadurecimento do código. Durante sessões de refatoração você pode aparecer com soluções melhores que as anteriores.
 
## Referências

- [Simple Programmer - Why KISS isn't easy](https://simpleprogrammer.com/kiss-one-best-practice-to-rule-them-all/)
- [The KISS Principle - Apache](https://people.apache.org/~fhanik/kiss.html)
