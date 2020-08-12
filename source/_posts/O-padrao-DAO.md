---
title: O padrão DAO
tags:
  - dao
  - design patterns
categories: engineering
thumb: database.svg
date: 2017-03-20 20:18:07
---
 
O padrão **DAO** (*Data access object*) fornece uma interface abstrata de comunicação com o banco de dados, ou qualquer outro mecanismo de persistẽncia de dados. Mapeando todas as chamadas da aplicação para a camada de persistência, classes **DAO** proverão operações de dados específicas sem expor o banco de dados em si. Este isolamento, respeita o princípio de responsabilidade única.
 
## Vantagens
 
A principal vantagem na utilização do padrão é a clara separação entre partes do código que não deveriam conhecer uma a outra. Todos os detalhes de implementação da comunicação entre a aplicação e o banco de dados ficam encapsuladas de forma que as demais partes do código não possuam acesso.
 
Sendo assim, alterações na persistẽncia de uma entidade pode ser aplicadas em apenas um lugar do código. 
 
Ao implementar o DAO como um intermediário entre a aplicação e o mecanismo de armazenamento, ganhamos a possibilidade de alterar completamente a tecnologia de persistência sem requerer muito esforço na camada de código da aplicação.
 
## Desvantagens
 
Possíveis desvantagens ao implementar o padrão são:
 
- [Leaky Abstractions](https://en.wikipedia.org/wiki/Leaky_abstraction) - Abstrações imperfeitas geradas devido ao aumento na complexidade das regras de negócio;
- [Código duplicado](https://en.wikipedia.org/wiki/Duplicate_code) - Ao duplicar operações de CRUD em classes distintas
- [Inversão de abstração](https://en.wikipedia.org/wiki/Abstraction_inversion) - Ao precisar reescrever funções já implementadas porém não expostas pelas interfaces para utilização em alto nível.
 
## Como funciona
 
A implementação “clássica” do padrão DAO, exige que tenhamos uma interface com as operações de banco de dados, a classe implementadora da interface e uma classe de domínio que represente o modelo (ou entidade do banco de dados).
 
No exemplo, vamos usar o padrão para demonstrar operações com a entidade **Customer**.
 
**Modelo:**
 
```java
public class Customer implements java.io.Serializable {
  int CustomerNumber;
  String name;
  String streetAddress;
  String city;
  ...
 
  /* getters e setters... */
  ...
}
```
 
**Interface de operações:**
 
```java
public interface CustomerDAO {
  public int insertCustomer(...);
  public boolean deleteCustomer(...);
  public Customer findCustomer(...);
  public boolean updateCustomer(...);
  public Collection selectCustomersTO(...);
  ...
}
```
 
**Classe implementadora:**
 
```java
/* Classe que se comunica com o banco de dados Postgres: */
public class CustomerPgDAO implements CustomerDAO {
  
  public CloudscapeCustomerDAO() {
    /* inicialização... */
  }
 
  public int insertCustomer(...) {
    /* lógica de inserção... */
    /* retorna o novo id criado ou -1 em caso de erro. */
  }
  
  public boolean deleteCustomer(...) {
    /* lógica de deleção... */
    /* retorna um boolean dizendo se a operação foi bem sucedida. */
  }
 
  public Customer findCustomer(...) {
    /* lógica para consulta de um registro da entidade Customer... */
    /* retorna uma instância da classe Customer ou nulo. */
  }
 
  public boolean updateCustomer(...) {
    /* lógica para atualizar um registro... */
    /* retorna um boolean dizendo se a operação foi bem sucedida. */
  }
 
  public Collection selectCustomersTO(...) {
    /* lógica para listar os registros de Customer... */
  }
  ...
}
```
 
**Código para consumir este DAO** 
 
Em outras partes da aplicação, onde você irá precisar interagir com as classes do padrão, você irá precisar de algo como:
 
```java
 
/* criando instância da classe: */
CustomerDAO dao =  new CustomerPgDAO();
 
/* criando um novo Customer: */
int newCustomer = dao.insertCustomer(...);
 
/* procurando algum Customer específico: */
Customer customer = dao.findCustomer(...);
 
/* modificando os valores do Customer obtido: */
customer.setAddress(...);
customer.setEmail(...);
 
/* aplicando a persistência através do DAO: */
dao.updateCustomer(customer);
 
/* excluir um Customer da persistência: */
dao.deleteCustomer(...);
...
```
 
Neste exemplo estamos lidando com persistência no banco de dados **Postgresql**, mas caso seja necessário adicionar suporte a outro banco de dados, basta criar uma nova classe implementadora da interface **CustomerDAO**, como foi feito em **CustomerPgDAO**, porém com a lógica de comunicação compatível com o novo banco de dados, como **MongoDB** por exemplo.
 
Do ponto de vista da camada de negócio, não será necessária nenhuma alteração!
 
Vale ressaltar também que pode ser utilizado o padrão de projeto **Factory Method** para encapsular a definição e criação de instâncias implementadoras da interface **CustomerDAO**, diminuindo ainda mais o nível de acoplamento no código.
 
## Conclusão
 
Apesar de existirem diversas ferramentas que já fazem o trabalho pesado para o desenvolvedor, é muito válido conhecer o padrão e os problemas que ele se propõe a resolver. Compreender os conceitos por trás das abstrações já existentes pode ser uma forma de aprimorar suas habilidades de programação, fornecendo maior compreensão sobre um problema e sua solução.
 
## Referências
 
- [Data Access Object on Wikipedia](https://en.wikipedia.org/wiki/Data_access_object)
- [Oracle's Core J2EE Patterns](https://www.oracle.com/java/technologies/dataaccessobject.html)
