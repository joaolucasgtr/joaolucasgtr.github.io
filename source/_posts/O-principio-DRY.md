---
title: O princípio DRY
tags: dry
categories: engineering
thumb: gears.svg
date: 2017-01-06 18:28:05
---


*Don’t repeat yourself* (**DRY**), ou *“Não Se Repita”*, é um princípio da área de desenvolvimento que visa reduzir repetição de código, utilizando abstrações e/ou normalização de dados.

O termo foi difundido no livro **The Pragmatic Programmer**, por Andy Hunt e Dave Thomas em 1999, e diz que:

> Cada bloco de informações deve ter uma representação oficial exclusiva e sem ambiguidades dentro de um sistema.

Quando o DRY é aplicado com sucesso, modificações em elementos do software são necessárias somente em um lugar e não requerem alterações em outros não relacionados. Além disso, elementos logicamente relacionados tendem a sofrer mudanças de maneira previsível e uniforme.

Outro ponto importante é que a aplicação do **DRY** não se limita apenas ao código produzido para sistemas. Ele pode ser aplicado em nível arquitetural, na modelagem de banco de dados, na documentação, em testes unitários..., ou seja, o conceito é abrangente o suficiente para ser aplicado em todos os estágios do desenvolvimento de software.

## Como surge a duplicação?

No livro, são indicados alguns casos onde a inserção de código duplicado é mais recorrente:

- **Duplicação imposta:** os desenvolvedores acham que não têm escolha – o ambiente parece pedir a duplicação.
- **Duplicação inadvertida:** Os desenvolvedores não percebem que estão duplicando informações.
- **Duplicação impaciente:** Os desenvolvedores ficam com preguiça e duplicam porque parece mais fácil.
- **Duplicação entre desenvolvedores:** Várias pessoas de uma equipe (ou de equipes diferentes) duplicam um bloco de informações.

As práticas de duplicação descritas aqui, opostas ao princípio **DRY**, são categorizadas como **WET**, podendo ser *We Enjoy Typing*, *We Edit Too much*, *Write Everything Twice*, entre outros. 

É interessante como esses acrônimos conseguem representar no mundo real exatamente o que propõem, sendo:

- **DRY** (seco): *Don’t repeat yourself* (Não se repita)
- **WET** (molhado): *We enjoy typing* (Nós gostamos de escrever)
 
## Como identificar uma violação do DRY?

A forma mais clara de identificar uma possível violação do princípio é no momento em que você aplica um `ctrl+c` + `ctrl+v`. Este simples ato pode representar a necessidade de aprimoramento estrutural em seu código.

Outro caso é quando uma alteração na regra de negócio faz com que seja necessário alterar o código em mais de um lugar. A violação fica evidente uma vez que a representação em código da regra não é única e livre de ambiguidades. E deveria ser.

Há violação do DRY também relacionada à escrita de comentários no código, já que cada vez que seu código precisa ser alterado, seu comentário também precisará, gerando assim trabalho redobrado sempre.

## Conclusão

Vimos como o **DRY** pode ser utilizado para evitar situações onde blocos de código executam conceitualmente a mesma função. Nelas, sempre que uma alteração é solicitada, diversos lugares do código devem ser alterados, aumentando a probabilidade de inserção de *bugs* e tempo gasto com desenvolvimento.

Esse conceito pode ser aplicado em qualquer escala, do nível mais baixo (código) até os níveis mais altos, evitando a construção de aplicações inteiras duplicadas. 

A busca por soluções genéricas que evitam a duplicação de trabalho, desencadeou a criação de ferramentas mais inteligentes, como linguagens de programação mais avançadas, Padrões de projeto, recursos avançados de manipulação de código, arquiteturas mais sofisticadas, etc.

Por isso, após muito tempo de reflexão, acredito ser, na minha opinião, o conceito mais importante na programação. 

## Referências

- [Don't repeat yourself on Wikipedia](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
- [Don't repeat yourself on WikiWikiWeb](https://wiki.c2.com/?DontRepeatYourself)