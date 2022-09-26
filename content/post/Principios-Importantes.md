---
title: Princípios Importantes
date: 2016-10-06 14:39:31
categories: [fundamentals]
tags: [engineering]
thumb: gears.svg
---

Se você é um desenvolvedor de software que almeja aperfeiçoar sua técnica de escrita de código (*sim, existem técnicas para escrever código*), então você provavelmente irá se deparar com diversos princípios de programação criados pela *Engenharia de Software*. Estes princípios foram criados com o intuito de aprimorar alguns atributos de qualidade de sistemas, que apesar de não funcionais influenciam diretamente no resultado final de um produto de software.

## Benefícios

Ao aplicar os princípios você estará automaticamente sendo beneficiado nos atributos:

- **Readability (Leitura)** - O código será mais facilmente entendido por outros membros do time de desenvolvimento.
- **Modularity (Modularidade)** - A divisão de funcionalidades em peças independentes (módulos) facilitará o processo de reuso e reduzirá a quantidade final de código escrito para a aplicação.
- **Maintainability (Manutenabilidade)** - O processo de manutenção será beneficiado com a melhoria da qualidade do código, além disso será diminuída a barreira de entrada de novos desenvolvedores nos projetos.
- **Extensibility (Extensibilidade)** - A inclusão de novas funcionalidades no sistema reduzirá consideravelmente a chance de efeitos colaterais devido ao código desacoplado.
- **Agility (Agilidade)** - Em decorrência da otimização dos processos de desenvolvimento, manutenção e extensão, os clientes poderão receber software de maneira mais ágil.

## Sobre os princípios

A lista a seguir contém apenas alguns princípios chave, que serão o suficiente para começar e observar o aprimoramento na qualidade de código produzido instantaneamente. A lista completa de artigos no Wikipedia você encontra aqui:

- *[Wikipedia's programming principles articles list](https://en.wikipedia.org/wiki/Category:Programming_principles)*.

### KISS

A sigla **KISS** é o acrônimo para "**keep it simple, stupid**" ou "**keep it stupid simple**". Este princípio visa reduzir casos de **Overengineering**, ou excesso de engenharia, que é muito comum entre desenvolvedores do nível júnior e pleno.

O foco principal é a simplicidade, evitando ao máximo toda complexidade desnecessária. Uma tática para aplicação do princípio é sempre quebrar grandes problemas em problemas menores, mais simples e mais compreensíveis.

### YAGNI

**You aren't gonna need it** (*você não vai precisar disso*) sugere aos desenvolvedores que não seja adicionado qualquer recurso ao *software* antes que ele seja realmente necessário. Segundo o princípio, o código deve se restringir aos requisitos já existentes e não em tentar prever solicitações futuras.

Este conceito foi proposto pela metodologia [Extreme Programming](http://www.extremeprogramming.org) de desenvolvimento ágil, que visa atacar a satisfação do cliente, pois em vez de entregar tudo que o cliente poderia desejar no futuro, será entregue somente o que ele precisa para hoje.

### Separation of concerns

**Separation of concerns** (*separação de responsabilidades*) é um princípio que visa separar o código em partes distintas, organizadas de forma lógica de acordo com sua responsabilidade. A aplicação correta deste princípio irá resultar em um grau maior de desacoplamento, tornando o *software* modular, onde cada módulo encapsula todo código relacionado à sua responsabilidade de forma lógica e coesa.

O princípio se aplica também à **Arquitetura de Software**, e foi utilizado como base para as definições de arquiteturas em camadas, por exemplo.

### SOLID

A sigla **SOLID**, em desenvolvimento de *software*, representa cinco princípios de *design* que visam facilitar a compreensão, desenvolvimento e manutenção de sistemas orientados a objetos. Aplicar o **SOLID** na prática significa aprimorar drasticamente a qualidade do código, tornando-o mais: legível, coeso, testável e reutilizável.

**Conceitos:**

| **Sigla** | **Nome** | **Descrição** |
| --------- | -------- | ------------- |
| **S** | [Single-responsibility principle](https://en.wikipedia.org/wiki/Single-responsibility_principle) | Uma classe deveria possuir somente uma responsabilidade e razão para mudar. |
| **O** | [Open–closed principle](https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle) | Entidades do *software* devem estar abertas à extensão mas fechadas para modificação |
| **L** | [Liskov substitution principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle) | Objetos em um programa devem poder ser substituídos por instâncias dos seus subtipos sem alterar seu funcionamento. |
| **I** | [Interface segregation principle](https://en.wikipedia.org/wiki/Interface_segregation_principle) | Muitas interfaces específicas são melhores que uma interface generalista. |
| **D** | [Dependency inversion principle](https://en.wikipedia.org/wiki/Dependency_inversion_principle) | É melhor depender de abstrações e não de implementações. |

Claramente, aplicar o **SOLID** em 100% do código que você escreve é uma tarefa extremamente difícil, e será ainda mais caso você fique adiando o dia de botar a mão na massa e aplicar os conceitos.

### Boy-Scout Rule

Os escoteiros possuem uma regra bem simples e clara:

> “Leave Things BETTER than you found them.” - Robert Baden Powell

Ao acampar, se o local de acampamento estiver uma bagunça, você deve limpá-lo independentemente de quem bagunçou, sempre deixando-o mais limpo do que estava quando você chegou.

Então Robert C. Martin adaptou essa regra para a programação, dizendo:

> "Leave the code cleaner than you found it" - Robert C. Martin

"Deixe o código mais limpo do que estava quando você o encontrou", significa sempre que possível aplicar refatorações de melhoria nos códigos, isso irá contribuir para a qualidade do projeto em geral e evitar a deterioração natural que os sistemas tendem a seguir durante seu período de vida.

*O artigo de [refatoração oportunista](https://martinfowler.com/bliki/OpportunisticRefactoring.html), de Martin Fowler, segue a mesma linha de raciocínio.*

### DRY

**Don't repeat yourself** (*Não se repita*) é o último, mas não menos importante, princípio desta lista. O princípio define que "cada porção de conhecimento em um sistema deve possuir uma representação **ÚNICA** em todo o sistema".

Utilizar o **DRY** significa trabalhar de forma mais inteligente, escrevendo menos código e produzindo valor no software de forma mais rápida ao reutilizar fragmentos genéricos.

Existe uma técnica bem simples para identificar possíveis violações do **DRY**: se você usou `crtl+c` + `crtl+v` em algum momento no seu código, é bem provável que você o esteja violando.

Violações do princípio são chamadas de soluções **WET** (*lol*), que podem significar: `write every time`, `write everything twice`, `we enjoy typing`, etc.

## Conclusão

Existem diversos outros princípios para desenvolvimento de *software* importantes, meu objetivo aqui foi somente trazer alguns para discussão e servir de guia para futuras pesquisas sobre o assunto.
