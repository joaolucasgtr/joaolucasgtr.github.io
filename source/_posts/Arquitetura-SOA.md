---
title: SOA - Service Oriented Architecture
tags: web
categories: architecture
thumb: architecture.svg
date: 2017-03-20 20:18:07
---

O termo **SOA** representa as iniciais de **Service Oriented Architecture** (*arquitetura orientada a serviços*), e representa um estilo arquitetural onde recursos da aplicação são disponibilizados por meio de serviços, através de um protocolo de comunicação pela rede.

## Serviços

**Serviço** é uma unidade de funcionalidade que pode ser acessado de forma remota ou local, e de forma independente. Um serviço possui quatro propriedades:

1. Representa uma atividade de negócio com uma resposta definida
2. É *self-contained* (independente)
3. É uma caixa preta para seus consumidores, já que não possuem conhecimento de como o serviço funciona por dentro
4. Pode consistir de outros serviços de camadas inferiores

Arquitetura orientada a serviços permite a integração entre sistemas distribuídos, mantidos e publicados de forma completamente separada. Está relacionada à ideia de API (*application programming interface*), um contrato de comunicação bem definido, que visa simplificar a integração entre *softwares*.

## Conceitos

Um manifesto foi publicado em outubro de 2009, onde são descritos seis valores listados a seguir:

- **Valor de negócio** tem mais importância do que à estratégia técnica;
- **Metas estratégicas** têm mais importância que benefícios específicos do projeto;
- **Interoperabilidade intrínseca** tem mais importância do que a integração personalizada;
- **Serviços compartilhados** têm mais importância que as implementações específicas;
- **Flexibilidade** tem mais importância que otimização;
- **Refinamento evolutivo** tem mais importância do que a busca pela perfeição inicial.
 
## Princípios

Apesar de não existirem padrões industriais que definem exatamente a composição de arquitetura orientada a  serviços, alguns princípios foram criados. 

Os mais comuns são:
 
**Autonomia de referência de serviços**

O relacionamento entre serviços é minimizado até o nível de que só conhecem a existência uns dos outros.

**Transparẽncia de localização de serviços**

Serviços podem ser chamados de qualquer local dentro da rede que estão contidos.

**Abstração de serviços**

Serviços agem como uma caixa preta, ou seja, a lógica interna fica escondida dos consumidores.

**Autonomia de serviços**

Serviços são independentes e controlam toda a funcionalidade que encapsulam.

**Falta de estado de serviços (Stateless)**

Serviços não armazenam estado, somente retornam o valor requisitado ou lançam alguma exceção, minimizando o consumo de recursos.

**Granularidade de serviços**

Este princípio diz que serviços devem possuir um tamanho adequado. Sua funcionalidade deve ser relevante.

**Normalidade de serviços**

Serviços são normalizados (como tabelas em banco de dados) para minimizar a possibilidade de redundância.

**Reusabilidade de serviços**

A lógica é dividida em vários serviços, para promover o reuso do código.
 
...entre outros.

## Implementações

A arquitetura em questão é implementada através de web services ou microserviços. Estes representam os blocos de funcionalidades acessíveis através de protocolos de comunicação de rede, que são independentes de plataforma ou linguagem de programação. 

Sendo assim, sistemas podem operar de forma independente e dinâmica, utilizando diversas tecnologias como:

- Web services baseados em WSDL e SOAP
- Messaging, com ActiveMQ, JMS, RabbitMQ
- REST over HTTP
- WCF (Windows Communication Foundation)
- gRPC
 
## Conclusão

Como vimos, a arquitetura orientada a serviços reforça vários conceitos de boas práticas, como reuso, modularidade, separação de responsabilidade, entre outros. Além disso, fatores como escalabilidade, flexibilidade e alta disponibilidade a transformam numa opção muito atrativa para o ambiente corporativo, devido à simplicidade na adoção e manutenção por parte das equipes de desenvolvimento. 
 
## Referências

- [*Service-oriented architecture on Wikipedia*](https://en.wikipedia.org/wiki/Service-oriented_architecture)
- [*SOA Manifesto*](http://soa-manifesto.org/)
