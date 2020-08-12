---
title: Como paginar resultados no MSSQL
date: 2015-04-4 17:32:33
categories: fundamentals
tags: database
thumb: database.svg
---

*Revisado em 01/2016*

Este documento tem como objetivo exemplificar duas maneiras distintas de se aplicar paginação utilizando o MSSQL Server.

**Objetivo:**

Reproduzir as operações de paginação corretas, de acordo com a tabela a seguir:

|**Limite** | **Página 1** | **Página 2**  | **Página 3**  |
| --------- | ------------ | ------------  | ------------  |
|  20       |  de 1 até 20 |  de 21 até 40 |  de 41 até 60 |
|  30       |  de 1 até 30 |  de 31 até 60 |  de 61 até 90 |

Onde **Limite** é a quantidade de itens exibidos por página.

### Calculando número de linhas

**Sintaxe:**

```sql
SELECT * FROM
  (
   SELECT ROW_NUMBER() OVER ( /* [ordenação] */ ) AS Linha
        , *
     FROM /* [tabela] */
  ) AS Linhas
 WHERE Linha >= /* [linha inicial] */ AND Linha <= /* [linha final] */

```

Desta maneira, o número atual da linha é retornado como uma coluna na tabela de resultados obtidos da *sub-query*. Isso permite a utilização dessa coluna para limitar os índices de início e fim dos resultados desejados.

Porém, utilizando essa abordagem, ainda é necessária a implementação de lógica para determinar esses valores, como demonstrado a seguir:

```sql
DECLARE @pagina1 INT = 3
      , @limite1 INT = 20

DECLARE @linha_inicial AS INT
      , @linha_final   AS INT

IF @pagina1 <> 1
  BEGIN
    SET @linha_inicial = ((@pagina1 - 1) * @limite1) + 1
  END
ELSE
  BEGIN
    SET @linha_inicial = @pagina1
  END

SET @linha_final = @limite1 * @pagina1

SELECT @linha_inicial AS inicio, @linha_final AS fim

```

**Exemplo:**

```sql
/*
   - Tratando e obtendo valores para os índices;
   - Obtendo um resultado paginado da tabela de usuários ordenados
     pelo Id de forma decrescente;
*/

DECLARE @pagina1 INT = 3
      , @limite1 INT = 20

DECLARE @linha_inicial AS INT
      , @linha_final   AS INT

IF @pagina1 <> 1
  BEGIN
    SET @linha_inicial = ((@pagina1 - 1) * @limite1) + 1
  END
ELSE
  BEGIN
    SET @linha_inicial = @pagina1
  END

SET @linha_final = @limite1 * @pagina1

SELECT * FROM
(
 SELECT ROW_NUMBER() OVER (ORDER BY Id DESC) AS Linha
      , *
   FROM Usuario
) AS Linhas
WHERE Linha >= @linha_inicial AND Linha <= @linha_final

```
---
### Uma "nova" abordagem

A "nova" abordagem se assemelha aos recursos já presentes em outros *SGBDs* há mais tempo, como **MySql** ou **Postgres**, onde é necessário apenas a utilização de um valor para o **OFFSET** (índice inicial de obtenção dos resultados) e **LIMIT** (quantidade de resultados obtidos por página).

**Sintaxe:**

```sql
 SELECT *
   FROM /* [tabela] */
  /* ordenação */
 OFFSET /* offset */ ROWS
  FETCH NEXT /* limit */ ROWS ONLY

```

Embora ainda seja necessária a utilização de lógica para obtenção dos valores de **OFFSET** e **LIMIT**, a sintaxe dessa abordagem é muito mais limpa e intuitiva, otimizando o tempo gasto em futuras refatorações.

Porém, esse recurso só está disponível na versão 12 ou posteriores do **MSSQL**.

**Exemplo:**

A seguir, uma implementação do exemplo dado anteriormente utilizando a nova sintaxe.

```sql
 DECLARE @pagina2 INT = 3
       , @limite2 INT = 20

 SELECT *
   FROM Usuario
  ORDER BY ErpId DESC
 OFFSET @limite2 * (@pagina2 - 1) ROWS
  FETCH NEXT @limite2 ROWS ONLY

```

### Conclusão

Os resultados obtidos nas duas *queries* de exemplo são equivalentes, exceto pelo fato de que na abordagem utilizando **ROW_NUMBER()** o número da linha é retornado como uma coluna extra na tabela de resultados.
