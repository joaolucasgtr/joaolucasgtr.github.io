---
title: Arquitetura em camadas
tags: [n-tier architecture, design patterns]
categories: [architecture]
thumb: architecture.svg
date: 2017-02-02 14:18:55
---

Construir um software utilizando a arquitetura em camadas significa desacoplar de forma lógica grupos de rotinas por responsabilidade. Cada camada então deverá possuir apenas uma responsabilidade e gerenciar suas dependências de forma interna. Uma camada superior pode usar os serviços de uma camada inferior, porém o oposto não pode ser aplicado.
É importante frisar que para a aplicação desta arquitetura ser bem sucedida, é necessário que o contexto exija a existência desse nível de desacoplamento, ou seja, aplicações de grande escala, onde desacoplamento, boa manutenibilidade e estruturas formais são um requisito básico.
 
## Sobre
 
Uma arquitetura em camadas, geralmente mencionada como n-tier architecture, ou multicamadas, é a forma de estruturar aplicações de forma distribuída. O modelo mais comum de utilização é a arquitetura em três camadas, sendo:
 
- Camada de apresentação
- Camada de negócio
- Camada de dados
 
cujo objetivo claro é obter uma estrutura mais flexível, onde cada camada pode ser facilmente substituída sem a necessidade de refatoração nas demais.

## Camada de apresentação
 
É o nível mais alto da aplicação, onde é possível visualizar e interagir com os dados gerenciados pela aplicação. Geralmente é chamada através de uma GUI (Graphical User Interface, ou interface gráfica de usuário), porém, em diversas aplicações a linha de comando é a camada de apresentação.

É de extrema importância que a única responsabilidade desta camada seja somente exibir os dados obtidos diretamente da camada inferior, a camada de regras de negócio, visando não ferir a premissa de que qualquer camada possa ser facilmente substituída.
 
### Padrões de projeto
 
A utilização de padrões de projeto apropriados para a camada de apresentação pode reduzir drasticamente o esforço de desenvolvimento do sistema. Além disso, adotar padrões amplamente conhecidos irá melhorar a manutenibilidade e entrada de novos colaboradores ao projeto.

Decisões mal tomadas nesta camada são, em particular, muito caras e custosas para se resolver, e você pode identificá-las quando:

- Aumentar a complexidade das interações do usuário, envolvendo relacionamentos não triviais entre entidades e páginas do sistema;
- Regras de negócios mudam e você precisa apresentar dados novos ou modificar funcionalidades existentes para novos usuários;
- Você precisar portar sua aplicação para outras plataformas.
 
Os padrões mais frequentemente utilizados na camada de apresentação são:

- **Observer:** fornecendo um mecanismo para que um objeto notifique outros de suas alterações, sem estabelecer fortes vínculos de dependências entre eles;
- **Page Controller:** utilizado por padrão no ASP.NET, onde cada página irá possuir sua classe controladora (Controller);
- **Model-View-Controller (MVC):** para casos de interfaces complexas, onde é necessário o reaproveitamento de dados em locais diferentes de visualização.
 
## Camada de negócio
 
A camada de lógica de negócios, ou *Business Layer*, se refere a implementação de regras de negócio ou requisitos do sistema. Aqui é escrito o código do “mundo real”, que determina como devem ser manipulados os dados da aplicação, como serão aplicadas as regras de validação e serve como camada de ligação entre as camadas de apresentação e dados.
É a camada com a maior probabilidade de mudança. 
 
### Padrões de projeto
 
A camada de negócio é que a vai possibilitar o maior número de casos de aplicação de padrões de projeto, por ser a camada “central” da aplicação. Assim, praticamente todos os padrões comportamentais podem ser encaixados nesta camada, basta estudar se é compatível com suas regras de negócio e aplicar.

Os padrões mais frequentemente utilizados na camada de negócio são: 

- **Facade:** fornecendo uma fachada simplificada que encapsula implementações complexas;
- **Chain of responsibility:** organizando a comunicação entre objetos solicitantes e fornecedores sem estabelecer dependência entre eles;
- **Strategy:** aprimorando a separação de responsabilidades por meio de abstrações e implementações concretas que não afetam estruturas já prontas;
- **Interpreter:** resolvendo expressões através de uma representação hierárquica de objetos;
- **Mediator:** encapsulando a maneira como os objetos interagem entre si

entre diversos outros...
 
## Camada de dados
 
Aqui é escrito todo código responsável por lidar com a persistência dos dados da aplicação, como bancos de dados, sistema de arquivos, etc. É necessário que a camada de dados possua uma API de comunicação que expõe métodos de acesso aos dados e evite totalmente possuir dependência de outras camadas. Isto irá facilitará o processo de substituição da camada de dados quando houver a necessidade de mudança de estrutura para melhorar o desempenho do sistema, por exemplo.
 
### Padrões de projeto
 
É necessário considerar algumas questões no design da camada de dados que podem afetar diversos aspectos do sistema, como segurança, desempenho e escalabilidade. Deve ser simples também o processo de manutenção e extensão assim que os requisitos começarem a mudar. 

Pontos a serem considerados:

- **Escolha da tecnologia de persistência:** existe realmente a necessidade de se usar um banco de dados? Se sim, esse banco deve ser relacional ou não? Se não, você pode gravar os dados em um arquivo XML ou JSON, ou no formato Chave-Valor?
- **Utilize abstração para diminuir o acoplamento:** isto pode ser alcançado utilizando Interfaces, com entradas a saídas bem definidas, ou classes abstratas para compartilhamento de lógicas genéricas;
- **Mantenha toda a lógica da camada de dados na camada de dados!** Esta camada deve esconder das outras as rotinas de conexão com banco de dados, criação e execução de queries e conhecimento da tecnologia de persistência;
- **Manipular exceções:** somente exceções relacionadas ao acesso a dados devem ser tratadas aqui e propagar para as camadas superiores as demais exceções para tratamento adequado.
 
Padrões mais frequentemente utilizados:

- **Singleton:** sendo a única fonte de se obter uma conexão ativa com o banco de dados em todo o sistema;
- **Data-Access-Objects (DAO):** fornecendo acesso à entidades persistidas de forma isolada segura;
- **Active Record:** onde cada entidade de dados é mapeada em uma classe com as operações de CRUD já embutidas;
- **Repository:** que fornece uma visão mais orientada a objetos do banco de dados
- **Unit of work:** mantendo uma lista de objetos afetados por uma transação para escrita coordenada das alterações.
 
## Conclusão

Neste artigo, pudemos observar alguns cenários de aplicação da arquitetura em camadas, visando aprimorar a forma como estruturamos sistemas. É possível notar como dois conceitos de boas práticas de programação trabalham muito bem juntos: a arquitetura em camadas e os padrões de projeto. Porém, isto não deve ser considerado como verdade absoluta para todos os casos. A aplicação indevida pode acabar gerando o efeito contrário ao proposto, burocratizando demais o processo de desenvolvimento e manutenção.

> Aplique conceitos certos diante de contextos certos.
 
## Referências:
 
- [Multitier architecture on wikipedia](https://en.wikipedia.org/wiki/Multitier_architecture)
- [Design and Implementation Guidelines for Web Clients](https://docs.microsoft.com/en-us/previous-versions/msp-n-p/ff647343(v=pandp.10)?redirectedfrom=MSDN)
- [Design Fundamentals, Chapter 8: Data Layer Guidelines](https://docs.microsoft.com/en-us/previous-versions/msp-n-p/ee658127(v=pandp.10)?redirectedfrom=MSDN)
 