---
title: Introdução ao versionamento semântico
date: 2016-05-04 13:49:11
tags: [semver]
categories: [fundamentals]
thumb: fundamentals.svg
---

[*SemVer.org 2.0.0*](http://semver.org/)

### Sumário

Dado um número de versão **[MAJOR].[MINOR].[PATCH]**, incremente a:

1. versão Maior (**MAJOR**): quando fizer mudanças incompatíveis na **API**,
2. versão Menor (**MINOR**): quando adicionar funcionalidades mantendo compatibilidade, e
3. versão de Correção (**PATCH**): quando corrigir falhas mantendo compatibilidade.

### Especificação (SemVer)

*palavras-chave definidas [aqui](#Palavras-chave-para-utilizacao-em-RFC’s-para-indicar-niveis-de-requisitos).*

*(...)*

* Um número de versão normal **DEVE** ter o formato de X.Y.Z, onde X, Y, e Z são inteiros não negativos, e **NÃO DEVE** conter zeros à esquerda. X é a versão Maior, Y é a versão Menor, e Z é a versão de Correção. Cada elemento **DEVE** aumentar numericamente. Por exemplo: 1.9.0 -> 1.10.0 -> 1.11.0.

* Uma vez que um pacote versionado foi lançado (*released*), o conteúdo desta versão **NÃO DEVE** ser modificado. Qualquer modificação **DEVE** ser lançado como uma nova versão.

* Versão de Correção Z (x.y.**Z** | x > 0) **DEVE** ser incrementado apenas se mantiver compatibilidade e introduzir correção de *bugs*. Uma correção de *bug* é definida como uma mudança interna que corrige um comportamento incorreto.

* Versão Menor Y (x.**Y**.z | x > 0) **DEVE** ser incrementada se uma funcionalidade nova e compatível for introduzida na API pública. **DEVE** ser incrementada se qualquer funcionalidade da API pública for definida como descontinuada. **PODE** ser incrementada se uma nova funcionalidade ou melhoria substancial for introduzida dentro do código privado. **PODE** incluir mudanças a nível de correção. A versão de Correção deve ser redefinida para 0(zero) quando a versão Menor for incrementada.

* Versão Maior X (**X**.y.z | X > 0) **DEVE** ser incrementada se forem introduzidas mudanças incompatíveis na API pública. **PODE** incluir alterações a nível de versão Menor e de versão de Correção. Versão de Correção e Versão Menor devem ser redefinidas para 0(zero) quando a versão Maior for incrementada.

### Por que usar Versionamento Semântico?

Sem a aderência a algum tipo de especificação formal, os números de versão são essencialmente inúteis para gerenciamento de dependências.

Dando um nome e definições claras às ideias acima, fica fácil comunicar suas intenções aos usuários de seu software.

**Exemplo:**

* Considere uma biblioteca chamada **CaminhaoBombeiros**;
* Ela requer um pacote versionado dinamicamente chamado **Escada**;
* Quando **CaminhaoBombeiros** foi criado, **Escada** estava na versão 3.1.0;
* Como **CaminhaoBombeiros** utiliza algumas funcionalidades que foram inicialmente introduzidas na versão 3.1.0, você pode especificar, com segurança, a dependência da **Escada** como maior ou igual a 3.1.0 porém menor que 4.0.0;
* Agora, quando **Escada** versão 3.1.1 e 3.2.0 estiverem disponíveis, você poderá lançá-los ao seu sistema de gerenciamento de pacote e saberá que eles serão compatíveis com os softwares dependentes existentes.

Como um desenvolvedor responsável você irá querer certificar-se que qualquer atualização no pacote funcionará como anunciado. O que você pode fazer é deixar o
*Versionamento Semântico* lhe fornecer uma maneira sensata de lançar e atualizar pacotes sem precisar atualizar para novas versões de pacotes dependentes, salvando-lhe tempo e aborrecimento.

### FAQ

Consultas, perguntas e respostas sobre o Versionamento Semântico.

> [**FAQ**](http://semver.org/#faq)

### Sobre

A Especificação da Semântica de Versionamento é autoria de [**Tom Preston-Werner**](http://tom.preston-werner.com/), criador do **Gravatars** e co-fundador do **GitHub**.

---

### Palavras chave para utilização em RFC's para indicar níveis de requisitos

[**RFCs - Request For Comments**](https://en.wikipedia.org/wiki/Request_for_Comments)

1. **DEVE:** Esta palavra, ou os termos **OBRIGATÓRIO** e **DEVERÁ**, significam que a definição é um requisito absoluto da especificação;

2. **NÃO DEVE:** Esta frase, ou os termos **NÃO DEVERÁ**, significam que a definição é um proibição absoluta da especificação;

3. **PODEM:** Esta palavra, ou o adjetivo **RECOMENDADO**, significam que podem existir motivos válidos para ignorar um item em particular, mas as implicações completas devem ser entendidas e cuidadosamente pesadas antes de escolher seguir um curso diferente;

4. **NÃO PODEM:** Esta frase, ou a frase **NÃO RECOMENDADO**, significam que podem existir motivos válidos onde o comportamento particular é aceitável ou até útil, mas as implicações completas devem ser entendidas e cuidadosamente pesadas antes de implementar um comportamento descrito com este rótulo.
