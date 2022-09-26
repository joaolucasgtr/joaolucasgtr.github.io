---
title: Refatoração
tags: [refactoring]
categories: [engineering]
thumb: gears.svg
date: 2017-02-15 22:53:12
---

O termo "refatorar" diz respeito à técnica de reestruturação de um trecho de código existente, modificando a sua estrutura interna sem modificar seu comportamento externo. Apesar de não parecer muito atraente para pessoas da área de gerência, a aplicação contínua desta prática poderá gerar efeitos bastante significativos na agilidade de trabalho do projeto alvo.

## O que é
No livro “Refactoring”, escrito por Martin Fowler em 2000, ele define:

**Substantivo:**

> “uma mudança feita na estrutura interna do software para deixá-lo mais fácil de entender e mais barato de modificá-lo, sem alterar seu comportamento observável.”

**Verbo:**

> reestruturar um software aplicando uma série de refatorações, sem alterar seu comportamento observável.

Refatoração não é somente uma nova palavra para “limpar seu código”, pois define uma técnica de aprimoramento da saúde da base de código. Esta técnica consiste em aplicar várias transformações pequenas, com poucas alterações. Após várias dessas transformações em sequência o resultado final certamente será significativo.

## Por que utilizar?

As intenções por trás da refatoração são: melhorar o *design* do código, melhorar a estruturação, reduzir complexidades, aplicar boas práticas, etc.

A refatoração é geralmente iniciada após a percepção de *bad smells*, ou seja, funções muito grandes, exagero de condicionais, identificação de códigos similares próximos, entre outros.

Outro ponto muito importante sobre a refatoração é a diminuição do custo para implementação de melhorias. Quando um software é lançado, existe a necessidade de continuar aprimorando-o constantemente, para correção de *bugs* e inclusão de novos recursos.

Numa base de código não saudável, a medida em que novos recursos vão sendo implementados, sem aplicação de refatoração, a velocidade do time de desenvolvimento irá diminuir constantemente. Por isso é importante manter a cultura de refatoração, para evitar o aumento de complexidade desnecessário.
 
## Quando refatorar?

Segundo o livro, a refatoração não deve ser uma tarefa especial lançada no planejamento, mas sim uma prática inserida no dia-a-dia de todos os desenvolvedores. O autor ainda cita dois exemplos sobre o *mindset* que utiliza para definir quando um código precisa ser refatorado:

**Ao adicionar um novo recurso a um sistema**

Primeiramente, é necessário olhar ao código já existente e se ele está estruturado de um jeito que seja simples incluir essa nova funcionalidade. Se não estiver, geralmente é melhor aplicar refatorações no código antes, para que a inclusão do recurso seja feita de forma simples. 

Assim o tempo total de sua tarefa deverá ser menor do que gastar horas tentando entender um código complexo e que, na próxima vez que um desenvolvedor passar por ele, terá de gastar muito tempo também tentando entendê-lo.

**Ao modificar um recurso já existente**

É sempre bom vasculhar a base de código já existente antes de começar. Pode ser que você encontre o que precisa em funções já definidas em outras partes do código, sobrando para você apenas o trabalho de chamá-las corretamente e evitar violar o princípio **DRY**. 

Caso o código que você precise alterar exija bastante esforço para compreensão, então é melhor aplicar refatorações para que outro desenvolvedor não seja exigido novamente por esse código (incluindo seu "eu" do futuro).

## Exemplos

A seguir, alguns exemplos de técnicas de refatoração presentes no livro:
 
### Extract method

**Problema:** Você possui um fragmento de código que pode ser agrupado:

```java
void printOwing() {
  printBanner();

  /* Print details. */
  System.out.println("name: " + name);
  System.out.println("amount: " + getOutstanding());
}
```

**Solução:** Agrupe este trecho em um novo método e chame-o no método antigo:

```java
void printOwing() {
  printBanner();
  printDetails(getOutstanding());
}

void printDetails(double outstanding) {
  System.out.println("name: " + name);
  System.out.println("amount: " + outstanding);
}
```

Esta técnica visa deixar seu código mais legível e reduzir a quantidade de linhas por método no código.

### Extract variable

**Problema:** Você possui uma expressão difícil de entender:

```java
void renderBanner() {
  if ((platform.toUpperCase().indexOf("MAC") > -1) &&
       (browser.toUpperCase().indexOf("IE") > -1) &&
        wasInitialized() && resize > 0 )
  {
    /* faça algo aqui... */
  }
}
```

**Solução:** Atribuir o resultado das expressões a variáveis cujo nome são auto-explicativos:

```java
void renderBanner() {
  final boolean isMacOs = platform.toUpperCase().indexOf("MAC") > -1;
  final boolean isIE = browser.toUpperCase().indexOf("IE") > -1;
  final boolean wasResized = resize > 0;

  if (isMacOs && isIE && wasInitialized() && wasResized) {
    /* faça algo aqui... */
  }
}
```

Esta outra técnica também visa aprimorar a legibilidade do código e reduzir a margem de erro ao lidar com múltiplas expressões.

## Replace temp with query

**Problema:** Você criou uma variável temporária para receber o valor de uma expressão:

```java
double basePrice = _quantity * _itemPrice;
if (basePrice > 1000)
  return basePrice * 0.95;
else
  return basePrice * 0.98;
```

**Solução:** Mova a expressão para um método novo e utilize o retorno deste método:

```java
if (basePrice() > 1000)
  return basePrice() * 0.95;
else
  return basePrice() * 0.98;

double basePrice() {
  return _quantity * _itemPrice;
}
```

Esta técnica é utilizada para deixar o código mais flexível e preparar o terreno para aplicar a **Extract Method** posteriormente.

## Consolidate conditional expression

**Problema:** Você possui múltiplas condições que geram o mesmo resultado:

```java
double disabilityAmount() {
  if (_seniority < 2) return 0;
  if (_monthsDisabled > 12) return 0;
  if (_isPartTime) return 0;
  
  /* compute the disability amount */
}
```

**Solução:** Consolide as condicionais em uma expressão única:

```java
double disabilityAmount() {
  if (isNotEligibleForDisability()) {
    return 0;
  }
  /* Compute the disability amount. */
}

boolean isNotEligableForDisability() {
  return (_seniority < 2)
      || _monthsDisabled > 12)
      || _isPartTime);
}
```

Assim você certamente irá evitar (ou até remover) trechos de códigos duplicados e possuir métodos simples para manutenções posteriores.

## Decompose conditional

**Problema:** Você possui uma condicional complexa:

```java
if (date.before (SUMMER_START) || date.after(SUMMER_END))
  charge = quantity * _winterRate + _winterServiceCharge;
else 
  charge = quantity * _summerRate;
```

**Solução:** Decomponha as partes complexas em métodos separados: a condição, o trecho executado quando a condição for positiva e o trecho executado quando for negativa:

```java
if (notSummer(date))
  charge = winterCharge(quantity);
else 
  charge = summerCharge (quantity);
```

Assim é possível dividir lógicas complexas, de forma que seja possível esquecer o que ocorre no `else` enquanto você estiver ocupado com o que deve ser executado dentro bloco `if`.

## Replace error code with Exception

**Problema:** Um método retorna um valor específico para indicar erro:

```java
int withdraw(int amount) {
  if (amount > _balance)
    return -1;
  else {
    _balance -= amount;
    return 0;
  }
}
```

**Solução:** Lance uma exceção:

```java
void withdraw(int amount) throws BalanceException {
  if (amount > _balance) 
    throw new BalanceException();
  
  _balance -= amount;
}
```

Lançar códigos de erros é algo obsoleto, herdado de linguagens procedurais. Lançar exceções irá lhe fornecer diagnósticos mais completos sobre as eventuais falhas ocorridas no sistema.

## Conclusão

Neste artigo pudemos introduzir alguns tópicos sobre o assunto "refatoração" e exemplificar algumas técnicas básicas. Um mergulho nos materiais originais irá expandir seu repertório de técnicas de escrita de código, que podem ser bem úteis em situações extremas, ou seja, te tornará um desenvolvedor mais seguro e capaz.

## Referências

- [Martin Fowler's Refactoring](https://refactoring.com/)
- [Code Refactoring on Wikipedia](https://en.wikipedia.org/wiki/Code_refactoring)
