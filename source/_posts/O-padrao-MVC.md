---
title: O padrão MVC
tags:
  - mvc
  - design patterns
categories: engineering
thumb: gears.svg
date: 2016-12-06 22:22:37
---


O padrão **MVC**, que significa **Model-View-Controller** (Modelo-Visão-Controlador), é um Design Pattern criado para aprimorar o desenvolvimento de interfaces de comunicação com o usuário.

Foi uma das primeiras abordagens a descrever o conceito de separação de responsabilidades, onde cada letra da sigla representa um componente que possui apenas uma responsabilidade bem definida.

**Relações entre os componentes:**

- **Modelo:** é o componente que representa os dados da aplicação. Possui a responsabilidade de gerenciá-los e validá-los, de acordo com regras de negócio;
- **Visão:** é a representação gráfica dos dados manipulados pela aplicação. Sua única responsabilidade é a de feedback ao usuário;
- **Controlador:** situa-se entre os outros dois componentes, permitindo que os mesmos se comuniquem durante a execução da aplicação.

Após a divisão da aplicação nestes três componentes, é esperado que eles se comuniquem da seguinte maneira:

- O modelo gerencia os dados da aplicação recebendo inputs do controlador;
- A visão exibe os dados presentes em seu modelo;
- O controlador recebe os inputs do usuário e os direciona para o modelo.

## Vantagens

Algumas das vantagens obtidas ao se aplicar o padrão MVC são:

- **Alta coesão:** a separação de componentes proposta pelo MVC permite o agrupamento de códigos similares de forma lógica;
- **Baixo acoplamento:** a própria natureza do padrão é reduzir o nível de acoplamento entre Modelo, Visão e Controladores;
- **Facilidade de manutenção:** em consequência da separação de responsabilidades torna o desenvolvimento futuro mais simples de ser compreendido;
- **Testabilidade:** com baixo acoplamento e separação de responsabilidades, cada componente pode ser testado de forma independente.

## Desvantagens

Apesar de ser um padrão extremamente popular e utilizado, ele também possui algumas desvantagens:

- **Navegabilidade:** a navegação pode se tornar complexa e requer que os desenvolvedores se adaptem à decomposição que o padrão exige;
- **Consistência de vários artefatos:** a decomposição em três componentes pode causar dispersão, exigindo maior cuidado dos desenvolvedores para que a consistência seja mantida;
- **Inflação de arquivos:** à medida que o projeto cresce, a quantidade de arquivos também crescerá, podendo dificultar a navegação entre eles;
- **Time to market:** por exigir conhecimento mais avançado, o início do projeto será mais demorado até que a equipe inteira assimile as exigências do padrão.

## Como funciona

Imagine que nos seja solicitado a implementação de um formulário de cadastro de clientes, e que após algum tempo de análise, chegamos à conclusão que será melhor aplicar o padrão **MVC**, baseado nas vantagens e desvantagens que ele possui. 

Um bom começo seria a classe de Modelo:

```java
public class Client {
  private String name;
  private String email;

  /* getters and setters... */
}
```

A visão representa o **GUI** propriamente dito. No nosso caso, será o terminal:

```java
public class ClientView {
  public void printClientDetails(String name, String email) {
    System.out.println("- Client:");
    System.out.println("    Name" + name);
    System.out.println("    E-mail" + email);
  }
}
```

O controlador recebe as instâncias do modelo e visão, e possui os métodos de manipulação de ambas as classes:

```java
public class ClientController {
  private Client model;
  private ClientView view;

  /* getter and setters... */

  public String getClientName() {
    model.getName();
  }

  public void setClientName(String name) {
    model.setName(name);
  }

  public String getClientEmail() {
    model.getEmail();
  }

  public void setClientEmail(String email) {
    model.setEmail(email);
  }

  public void updateView() {
    view.printClientDetails(model.getName(), model.getEmail());
  }
}
```

No método principal, demonstramos a utilização do padrão:

```java
public static void main(String[] args) {
  /* create a Client instance: */
  Client client = new Client("John Doe", "john_doe@email.com");

  /* create a View instance: */
  ClientView view = new ClientView();

  /* create a Controller instance: */
  ClientController controller = new ClientController(model, view);

  controller.updateView();
  /* console:
     - Client:
       Name: John Doe
       E-mail: john_doe@email.com
  */

  controller.setClientName("John moe");
  controller.setClientEmail("john_moe@email.com");

  controller.updateView();
  /* console:
     - Client:
       Name: John Moe
       E-mail: john_moe@email.com
  */
}
```

Pode parecer muito trabalho para algo simples e realmente é. Porém, se o objetivo for criar um projeto grande, com diversas interfaces, este padrão irá ajudar a manter a base de código estruturada de forma mais coesa e com com melhor índice de manutenibilidade.

## Observações

É extremamente comum encontrar materiais descrevendo o padrão MVC como sendo um padrão arquitetural e isso é um erro. MVC é um padrão de projeto e é frequentemente confundido com arquitetura em camadas. 

Um exemplo claro desse equívoco é encontrado em tutoriais que inserem códigos de acesso ao banco de dados em classes de Modelo. O MVC é um padrão destinado à criação de interfaces, o que numa arquitetura multi camadas significa a camada de apresentação. 

Misturar códigos de camadas diferentes certamente irá gerar efeitos contrários aos propostos: aumento na complexidade do código, falta de coesão, alto acoplamento, etc.

## Referências

- [Model-view-controller on Wikipedia](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)
- [Martin Fowler about GUI Architectures](https://martinfowler.com/eaaDev/uiArchs.html)
