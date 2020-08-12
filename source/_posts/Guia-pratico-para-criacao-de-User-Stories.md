---
title: Guia prático para criação de User Stories
date: 2016-03-08 23:58:59
tags: agile
categories: fundamentals
thumb: fundamentals.svg
---

As estórias de usuário, ou [**User Stories**](https://en.wikipedia.org/wiki/User_story), são utilizadas para organização de requisitos por parte do **PO** ([*Product Owner*](https://pt.wikipedia.org/wiki/Scrum)) e tem como foco principal o objetivo do usuário.

Estórias fracionam os requisitos e facilitam a estimação do esforço gasto para realização do objetivo descrito, sendo curtas, simples e claras. Caso uma estória acabe ficando extensa, isso é um sinal de que ela pode ser divida em outras.

### Princípio INVEST

O acrônimo [**INVEST**](https://en.wikipedia.org/wiki/INVEST_(mnemonic)) foi criado para definir as características de uma boa estória, como demonstrado a seguir:

| Letra | Significado | Resumo |
| --- | --- | --- |
| **I** | Independent | Uma boa estória deve ser independente de outras. |
| **N** | Negotiable | Até o dia da implementação, a estória pode ser modificada ou reescrita. |
| **V** | Valuable | Deve entregar algum valor para o usuário final. |
| **E** | Estimable | O prazo para entrega deve sempre ser estimável. |
| **S** | Small | Não deve demorar mais do que um *Sprint* para ser entregue. |
| **T** | Testable | Se não puder testar as alterações entregues, não saberá se funcionam bem, certo? |

### Definições e exemplos

Para construir uma estória, basta definir o **autor**, a **ação**,a funcionalidade desejada, ou seja, o **resultado**, e a sua **prioridade**.

- **Autor** - O proprietário da estória, a pessoa interessada na funcionalidade. Recomendado descrição de forma bem clara.

- **Ação** - A ação necessária para que o autor possa alcançar seu objetivo.

- **Resultado** - Resultado que ator espera ao executar a ação, de acordo com sua ótica.

- **Prioridade** - Estórias com prioridade alta serão incluídas mais cedo nos *Sprint's*.

**Modelo:**

    Como um [autor], eu quero [ação] para que [resultado].
    Prioridade: [alta, média, baixa].

**Exemplo de um sistema de biblioteca:**

    Como um "vendedor responsável pelo setor de livros",
    eu quero "procurar por livros filtrando por nome",
    para que possa "verificar se o livro x está disponível".
    Prioridade: "alta".

**Exemplo de sistema de aluguel de filmes:**

    Como um "cliente",
    eu quero "ver os filmes disponíveis para locação",
    para que possa "alugá-lo".
    Prioridade: "alta".

**Exemplo de sistema de cadastro de clientes**

    Como um "vendedor",
    eu quero "consultar meus clientes pelo CNPJ",
    para "negociar descontos para pessoa jurídica".
    Prioridade: "média".
