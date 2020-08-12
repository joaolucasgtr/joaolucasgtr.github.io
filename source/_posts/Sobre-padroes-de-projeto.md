---
title: Sobre padrões de projeto
date: 2016-12-01 20:44:42
tags: design patterns
categories: engineering
thumb: gears.svg
---
 
Na engenharia de software, um *design pattern* (ou padrão de projeto), é uma solução de alto nível já definida para problemas recorrentes no campo da programação. Não representa um *framework*, código fonte ou algo do tipo, mas sim um *template* que descreve como deverá ser aplicado para solucionar o problema a que se propõe.
 
Mas a explosão de popularidade ocorreu mesmo após o lançamento do livro [Design Patterns: Elements of Reusable Object-Oriented Software](https://en.wikipedia.org/wiki/Design_Patterns) (ou Padrões de Projeto: soluções reutilizáveis de software orientado a objetos), de 1994, escrito pela "*Gang of four*": Erich Gamma, Richard Helm, Ralph Johnson, John Vlissides. A edição original traz a definição de vinte e três padrões clássicos e você encontra uma lista resumida no [final deste artigo](#Lista-de-padroes-por-categoria).
 
## Sobre o livro
 
O livro possui duas partes, sendo a primeira explorando as capacidades e armadilhas da programação orientada a objetos, e a segunda abordando os vinte e três padrões. Para aproveitar a leitura é necessário que você já possua proficiência nos conceitos de orientação a objetos, para que você não tenha que interromper a leitura sempre que for mencionado algo como polimorfismo, herança ou interface, por exemplo.
 
Por outro lado, não será uma leitura técnica avançada, pois os padrões são descritos com soluções simples e elegantes, visando suprir algumas necessidades da programação orientada a objetos. Sendo assim, não são necessários recursos incomuns ou truques fantásticos de programação para implementá-los, ou seja, todos os padrões podem ser escritos usando recursos básicos das linguagens de programação.
 
## Benefícios
 
Assim que entender como utilizar os padrões e sua reação for um "A-Ha!" (e não um "Ahn?"), provavelmente nunca mais verá a orientação a objetos da mesma forma. Você terá diversos *insights* que o ajudarão a produzir *designs* mais flexíveis, modulares, reutilizáveis e mais compreensíveis. Afinal, este é o seu objetivo, certo?
 
Construir *software* é difícil, construir *software* orientado a objetos de forma reutilizável é ainda mais difícil. Você deve criar objetos pertinentes, classes com a granularidade correta, definir boas *interfaces* e suas heranças, e ainda estabelecer relacionamento entre essas entidades. Você deve evitar o *redesign* ou ao menos tentar minimizá-lo. Desenvolvedores experientes lhe dirão que um *design* flexível e reutilizável é praticamente impossível de se fazer da forma "certa" da primeira vez.
 
O propósito do livro é registrar experiências adquiridas anteriormente, transformando-as em padrões, que facilitam a criação de novos sistemas, expressando técnicas bem sucedidas.
 
Padrões te ajudam a ter mais alternativas de soluções na hora de escrever código e ainda facilitam o processo de documentação e manutenção, fornecendo especificações explícitas de classes e interação entre os objetos.
 
## Definindo um padrão
 
Cada padrão sistematicamente nomeia, explica e avalia um *design* importante e recorrente. O objetivo é capturar o *design* de forma que pessoas possam utilizá-lo de forma eficiente.
 
Em geral, um padrão possui quatro elementos essenciais:
 
- **Nome -** O nome do padrão é utilizado para descrever um problema, a solução e as consequências, e deve ser escrito em uma palavra ou duas. Também ajuda na comunicação em um nível alto de abstração e foi um dos pontos mais difíceis durante a produção do livro.
- **Problema a ser resolvido -** O problema descreve quando aplicar o padrão e seu contexto. Algumas vezes o problema irá incluir uma lista de condições que devem ser atendidas antes de aplicar o padrão.
- **Solução dada pelo padrão -** A solução descreve os elementos que constituem o *design*, seus relacionamentos, responsabilidades e colaborações. A solução não descreve um *design* concreto e particular, uma vez que os padrões são *templates* abstratos para serem aplicados em diversas situações diferentes.
- **Consequências -** As consequências são os resultados e os *trade-offs* da aplicação do padrão e devem sempre ser consideradas antes de decidir a aplicação do padrão.
 
### Como escolher um Design Pattern
 
Com mais de vinte padrões no catálogo, pode parecer difícil encontrar um que seja adequado ao seu problema de *design*. A seguir, algumas abordagens diferentes para definir qual padrão é a melhor escolha para o seu problema:
 
1. Considere como padrões resolvem problemas de *design*, quais são os objetos apropriados, a granularidade desses objetos e *interfaces* relacionadas. Estudar estes pontos é um bom ponto de partida para encontrar um padrão adequado.
2. Leia através de cada intenção dos padrões para encontrar um ou mais que pareçam relevantes para o seu problema. Utilize o catálogo no próximo tópico para facilitar sua busca.
3. Estude como os padrões se relacionam. Estudar os relacionamentos podem te guiar na direção certa dos padrões ou grupos de padrões. Imagem de referência no final do artigo.
4. Estude os padrões por seu propósito. Existem três categorias diferentes de padrões: criacionais, estruturais e comportamentais. Isto com certeza irá facilitar a busca ao comparar padrões diferentes agrupados por propósito.
5. Examine as [causas de *redesign*](https://blogs.agilefaqs.com/2008/09/05/common-causes-of-redesign/), pois elas possuem padrões relacionados criados para resolver estes problemas.
6. Considere o que pode ser variável no seu *design*. Em vez de considerar o que poderia forçá-lo ao *redesign*, considere o que quer que seja possível mudar sem *redesign*. O foco aqui está em encapsular o conceito que irá variar, tema de muitos padrões.
 
## Lista de padrões por categoria
 
### Criacionais
 
São padrões que criam objetos, em vez de ter que instanciá-los diretamente. Isto proporciona ao programa maior flexibilidade em decidir quais objetos precisam ser criados para um determinado caso.
 
- [**Abstract factory**](https://en.wikipedia.org/wiki/Abstract_factory_pattern) agrupa *factories* que possuem um tema em comum.
- [**Builder**](https://en.wikipedia.org/wiki/Builder_pattern) constrói objetos complexos separando construção e representação.
- [**Factory Method**](https://en.wikipedia.org/wiki/Factory_method_pattern) constrói objetos sem especificar exatamente qual classe utilizar.
- [**Prototype**](https://en.wikipedia.org/wiki/Prototype_pattern) cria objetos clonando outros existentes.
- [**Singleton**](https://en.wikipedia.org/wiki/Singleton_pattern) restringe a criação de um objeto para uma única instância de classe.
 
### Estruturais
 
Estes visam composição de objetos e classes. Utilizam herança para compor *interfaces* e definir maneiras de compor objetos e obter novas funcionalidades.
 
- [**Adapter**](https://en.wikipedia.org/wiki/Adapter_pattern) permite classes com *interfaces* incompatíveis a trabalharem juntas, criando sua própria *interface* a partir de uma classe já existente.
- [**Bridge**](https://en.wikipedia.org/wiki/Bridge_pattern) desacopla abstração de implementação para que as duas possam variar independentemente.
- [**Composite**](https://en.wikipedia.org/wiki/Composite_pattern) compõe zero ou mais objetos similares, para que possam ser manipulados como um só.
- [**Decorator**](https://en.wikipedia.org/wiki/Decorator_pattern) dinamicamente adicionar ou sobrescreve o comportamento de um método já existente em um objeto.
- [**Facade**](https://en.wikipedia.org/wiki/Facade_pattern) provê uma *interface* simplificada para uma implementação grande de código.
- [**Flyweight**](https://en.wikipedia.org/wiki/Flyweight_pattern) reduz o custo de criação e manipulação de um grande número de objetos parecidos.
- [**Proxy**](https://en.wikipedia.org/wiki/Proxy_pattern) provê uma forma para que outro objeto controle o acesso, reduza custos e reduza a complexidade.
 
### Comportamentais
 
A maioria destes padrões se preocupa com a comunicação entre objetos.
 
- [**Chain of responsibility**](https://en.wikipedia.org/wiki/Chain-of-responsibility_pattern) delega comandos para uma cadeia de processamento de objetos.
- [**Command**](https://en.wikipedia.org/wiki/Command_pattern) cria objetos que encapsulam ações e parâmetros.
- [**Interpreter**](https://en.wikipedia.org/wiki/Interpreter_pattern) implementa uma linguagem especializada.
- [**Iterator**](https://en.wikipedia.org/wiki/Iterator_pattern) acessa os elementos de uma coleção sem expor sua representação interna.
- [**Mediator**](https://en.wikipedia.org/wiki/Mediator_pattern) permite desacoplamento entre classes, sendo a única a ter conhecimento detalhado de seus métodos.
- [**Memento**](https://en.wikipedia.org/wiki/Memento_pattern) provê habilidade de restaurar um objeto ao seu estado anterior (`ctrl+z`).
- [**Observer**](https://en.wikipedia.org/wiki/Observer_pattern) permite comunicação entre objetos através de eventos.
- [**State**](https://en.wikipedia.org/wiki/State_pattern) permite um objeto a mudar seu comportamento quando seu estado interno altera.
- [**Strategy**](https://en.wikipedia.org/wiki/Strategy_pattern) permite escolher dinamicamente um algoritmo, de uma família, em tempo de execução.
- [**Template**](https://en.wikipedia.org/wiki/Template_method_pattern) define um algoritmo esqueleto como uma classe abstrata, permitindo que subclasses implementem o comportamento concreto.
- [**Visitor**](https://en.wikipedia.org/wiki/Visitor_pattern) separa um algoritmo de uma estrutura de objeto ao mover-se hierarquicamente dentre métodos de um objeto.
 
## Por onde começar?
 
Se você ainda não é um desenvolvedor com experiência, então comece com os mais simples e comuns, listados a seguir:
 
- Abstract Factory
- Adapter
- Composite
- Decorator
- Factory Method
- Observer
- Strategy
- Template Method
 
## Conclusão
 
A importância dos padrões de projetos é reconhecida globalmente por oferecer soluções inteligentes para problemas recorrentes. Dificilmente você encontrará sistemas orientados a objetos que não utilizem ao menos um dos padrões apresentados neste artigo, sendo que em sistemas grandes a tendendência é que vários padrões tenham sido utilizados.
 
Aplicar padrões de projetos é considerada uma boa prática de engenharia de *software* pois evita que você viole o princípio **DRY** (don't repeat yourself), ao poupar a si mesmo de gastar horas pensando em soluções que já foram criadas, aplicadas e testadas em ambientes de produção ao redor do globo.
