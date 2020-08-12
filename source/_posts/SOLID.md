---
title: SOLID (com exemplos)
tags: solid
categories: engineering
thumb: gears.svg
date: 2017-02-20 23:56:22
---

Após mencionar o acrônimo **SOLID** na publicação sobre [Princípios importantes](), resolvi escrever um artigo mais detalhado para abordar cada conceito de forma particular e com exemplos. Assim fica mais fácil compreender e absorver o valioso conteúdo presente nos conceitos.

## S - Single Responsibility Principle (SRP)

O **princípio da responsabilidade única** é um conceito que diz que cada módulo ou classe deveria possuir apenas responsabilidade sobre uma parte da funcionalidade de um *software*, e que essa responsabilidade deveria ser encapsulada pela classe, módulo ou função.

*Robert C. Martin* expressa o princípio como:

> "A class should have only one reason to change." (Uma classe deveria ter apenas um motivo para mudar.)

### Objetivo

O objetivo aqui é evitar a criação de uma [**God class** (ou *God object*)](https://en.wikipedia.org/wiki/God_object), as classes "Deusas" que possuem diversas responsabilidades e funções muito além do que deveriam ser o seu escopo.

### Exemplo

```cs
public class Employee
{
  public int Employee_Id { get; set; }
  public string Employee_Name { get; set; }

  public bool InsertIntoEmployeeTable(Employee em)
  {
    /* Insert into employee table. */
    return true;
  }

  public void GenerateReport(Employee em)
  {
    /* Report generation with employee data using crystal report. */
  }
}
```

Esta classe viola o **SRP** ao ser responsável por duas operações distintas:

1. Lidar com operações de banco de dados;
2. Lidar com a operação de gerar relatórios sobre um empregado.

De acordo com o **SRP**, o ideal seria criar duas classes, com responsabilidades mais coerentes, da seguinte forma:

```cs
public class Employee
{
  public int Employee_Id { get; set; }
  public string Employee_Name { get; set; }

  public bool InsertIntoEmployeeTable(Employee em)
  {
    /* Insert into employee table. */
    return true;
  }
}

public class Reporter
{
  public void GenerateReport(Employee em)
  {
    /* Report generation with employee data using crystal report. */
  }
}
```

Assim, alterações na geração de relatórios não irão requerer mudanças na classe **Employee**, e vice-versa.

## O - Open closed principle (OCP)

O **princípio aberto / fechado** diz que entidades do *software* (classes, módulos, funções, etc.) devem estar **abertas** para extensão, porém **fechadas** para alteração, assim uma entidade irá permitir que seu comportamento seja estendido sem modificar seu código original.

### Objetivo

Aumentar o nível de desacoplamento e segurança, evitando que alterações sejam feitas posteriormente em classes já presentes nos sistemas.

### Exemplo

```cs
public class Reporter
{
  public string ReportType { get; set; }

  public void GenerateReport(Employee em)
  {
    if (ReportType == "CRS")
    {
      /* Report generation with employee data in Crystal Report. */
    }
    if (ReportType == "PDF")
    {
      /* Report generation with employee data in PDF. */
    }
  }
}
```
Esta classe claramente viola o **OCP**, pois uma vez que seja recebido um requisito para geração de relatório em outro formato, `csv` por exemplo, deveríamos obrigatoriamente ter que alterá-la para incluir mais uma condição no método.

Aplicando o **OCP**, poderíamos criar uma *interface* e delegar a lógica de geração de relatórios somente para os implementadores. Com isto, incluir um novo tipo de relatório consiste apenas em criar uma nova classe implementadora de *interface*, sem gerar alterações na classe anterior.

```cs
public class IReportGenerator
{
  public virtual void GenerateReport() { /* From base */ }
}

public class CrystalReportGenerator : IReportGenerator
{
  public override void GenerateReport()
  {
    /* Generate crystal report. */
  }
}

public class PDFReportGenerator : IReportGenerator
{
  public override void GenerateReport()
  {
    /* Generate PDF report. */
  }
}

public class Reporter
{
  public void GenerateReport(IReportGenerator generator)
  {
    generator.GenerateReport();
  }
}

```

## L - Liskov substitution principle (LSP)

O **princípio da substituição de Liskov** diz que a substituição de uma classe derivada por sua classe base não deve afetar o comportamento correto do sistema.

### Objetivo

Manter a coesão entre as abstrações do código, evitando extensões de interfaces desnecessárias.

### Exemplo

```cs
public class Employee
{
  public string GetName()
  {
    return "Base name";
  }
}

public class CasualEmployee : Employee
{
  public override string GetName()
  {
    return "My name is CasualEmployee";
  }
}

public class ContractualEmployee : Employee
{
  public override string GetName()
  {
    return "My name is ContractualEmployee";
  }
}

public static void Main(string[] args)
{
  var employees = new List<Employee>
  {
    new Employee(),
    new CasualEmployee(),
    new ContractualEmployee()
  };

  foreach (var e in employees)
    Console.WriteLine(e.GetName());
}
```
As classes derivadas de **Employee**, neste exemplo, podem ser substituídas pela classe base sem gerar efeitos indesejados no código, pois não há violação do **LSP**.

Este princípio está altamente ligado ao próximo tópico da lista, por se tratar de escrever abstrações de forma mais coesa.

## I - Interface segregation principle (ISP)

O **princípio da segregação de interfaces** diz que uma classe não deve implementar métodos de uma *interface* que ele não irá usar.

### Objetivo

Optar pela criação de várias *interfaces* específicas sobre uma *interface* generalista, evitando obrigar que classes implementem métodos irrelevantes para si mesmas.

### Exemplo

```cs
interface IEmployee
{
  string GetName();
  int GetContractId();
}
```
Se inserirmos o método **GetContractId** na *interface* **Employee** estaremos violando o princípio **ISP** pois somente empregados do tipo **ContractualEmployee** possuirão um número de contrato. A classe **CasualEmployee** irá ser forçada a implementar um método que ela nunca utilizará. Sendo assim, o ideal seria:

```cs
interface IEmployee
{
  string GetName();
}

interface IContractualEmployee : IEmployee
{
  int GetContractId();
}

public class ContractualEmployee : IContractualEmployee { }

public class CasualEmployee : IEmployee { }
```

## D - Dependency inversion principle (DIP)

O **princípio da inversão de dependência** é uma forma poderosa de desacoplamento de código. Nele é dito que classes não devem dependender de implementações, mas sim de abstrações:

> Módulos de alto nível não deveriam depender de módulos de baixo nível. Ambos deveriam depender de abstrações (interfaces).
> Abstrações não deveriam depender de detalhes. Detalhes (implementação concreta) deveriam depender de abstrações.

### Objetivo

O objetivo principal do **DIP** é reforçar o desacoplamento, evitando que classes possuam dependências fortes com outras classes.

### Exemplo

Imagine que vamos precisar enviar notificações para usuários após alterações realizadas no banco de dados.

```cs
public class Email
{
  public void SendMail() { }
}

public class Notification
{
  private Email _email;

  public Notification()
  {
    _email = new Email();
  }

  public void PromotionalNotification()
  {
    _email.SendMail();
  }
}
```
Assim a classe **Notification** depende completamente da classe **Email**. Em qualquer lugar que for necessário o envio de notificações, será necessário também a inclusão da classe **Email**. O forte acoplamento dificulta também a inclusão de outros métodos de notificação.

```cs
interface INotifier
{
  void SendNotification();
}

public class Email : INotifier
{
  public void SendNotification() { /* send email notification */ }
}

public class SMS : INotifier
{
  public void SendNotification() { /* send sms notification */ }
}

public class Notification
{
  private INotifier _notifier;

  public Notification(Type notifierType)
  {
    if (typeof(notifierType) == typeof(Email))
      _notifier = new Email();
    if (typeof(notifierType) == typeof(SMS))
      _notifier = new SMS();
  }

  public void Notify()
  {
    _notifier.SendNotification();
  }
}
```
Assim está um pouco melhor, porém o objetivo ainda não foi alcançado pois a classe **Notification** ainda depende das classes implementadoras da *interface* **INotify**. Para aplicar o desacoplamento total devemos utilizar a técnica de injeção de dependência, que pode ser feita de três formas:

1. **Construtor:**

```cs
public class Notification
{
  private INotifier _notifier;

  public Notification(INotifier notifier)
  {
    _notifier = notifier;
  }

  public void Notify()
  {
    _notifier.SendNotification();
  }
}
```

2. **Propriedade:**

```cs
public class Notification
{
  private INotifier _notifier;

  public INotifier Notifier
  {
    private get;
    set { _notifier = value; }
  }

  public void Notify()
  {
    _notifier.SendNotification();
  }
}
```

3. **Método:**

```cs
public class Notification
{
  public void Notify(INotifier notifier)
  {
    notifier.SendNotification();
  }
}
```

## Conclusão

Podemos perceber que alguns dos princípios são bem próximos e com um tempo de prática e aplicação, você com certeza irá notar a evolução na qualidade do código que escreve. Aplicar as boas práticas pode não ser do interesse de todos, o que libera espaço para que você se destaque quando os resultados começarem a aparecer.

## Referências

- [SOLID on Wikipedia](https://en.wikipedia.org/wiki/SOLID)
- [SOLID Principle with C# Example](https://www.codeproject.com/Tips/1033646/SOLID-Principle-with-Csharp-Example)
