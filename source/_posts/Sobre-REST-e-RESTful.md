---
title: Sobre REST e RESTful
date: 2015-02-26 16:53:33
categories: architecture
tags: web
thumb: architecture.svg
---
 
Primeiramente introduzido por Roy Fielding em sua dissertação de mestrado de 2000, o termo *REST* representa um estilo arquitetural focado na troca de dados entre clientes e servidores pela *web*. Note que o termo correto para definição de *REST* é estilo arquitetural, não é um protocolo e nem um padrão de projeto.

O ponto chave é que o servidor não precisa saber nada sobre a aplicação em si, deixando-o altamente desacoplado e facilmente integrável por clientes diversos.

> O termo REST é um acrônimo para **Re**presentational **S**tate **T**ransfer (Transferência de Estado Representacional), porém o legal é que a palavra REST significa descansar, que é exatamente o comportamento de uma api REST.

## Princípios

No capítulo cinco, Roy descreve os princípios básicos de sua tese, que são:

- **Client-Server** (Cliente-Servidor) - Aplicações REST possuem arquitetura Cliente-Servidor, obedecendo o conceito de *Separação de responsabilidades*. Isto facilita o processo de evolução, portabilidade e escalabilidade de software.
- **Stateless** (Sem estado) - O servidor não deve manter nenhum estado a respeito dos clientes. Cada requisição deve conter toda informação necessária para entendimento e processamento da mesma.
- **Cache** - Para aprimorar a eficiência da rede, servidores podem marcar respostas como *cacheable* (cacheáveis), para que os clientes possam reutilizá-las posteriormente.
- **Uniform Interface** (Interface uniforme) - A característica central que difere o REST de outras arquiteturas *web* é sua ênfase em uma interface uniforme de comunicação.
- **Layered System** (Sistema em camadas) - Compor a aplicação em camadas, onde cada componente não consegue acessar código presente fora de sua camada, facilita a adição de balanceadores de carga e *proxies*, para aprimorar a performance e segurança.

Um serviço é dito **RESTful** quando atende aos princípios descritos acima, definidos por Roy. A combinação destes princípios criam um tipo de aplicação bem específico, focado em escalabilidade, performance e segurança.

## Protocolo

O protocolo utilizado para comunicação é o **HTTP**. Apesar de existir há mais de vinte anos, o protocolo recebeu diversas atualizações para modernização e aprimoramento semântico. Sugestões de criação de novos verbos, pelo próprio Roy, foram adotadas e implementadas, permitindo que a leitura ficasse bem mais próxima da nossa realidade. Requisições como:

- **GET** - `http://server:8080/users`
- **DELETE** - `http://server:8080/users/john`
- **POST** - `http://server:8080/users` - `data={ name: stevie }`

são extremamente explícitas no que se propõem a fazer.

## REST vs RESTful

Após a definição do que é **REST** e **RESTful**, pode ser que ainda exista dúvida sobre as diferenças entre os termos. Sabemos que **REST** é um estilo arquitetural e **RESTful** é o serviço que implementa **REST**. Porém, somente pode-se dizer que uma api é **RESTful** se a mesma obedecer a todos os princípios definidos por Roy.

Muitos desenvolvedores podem não sentir nenhum tipo de incômodo ao se deparar com *endpoints* como estes:

- **GET** - `http://server:8080/users/123/delete`
- **PUT** - `http://server:8080/users`

Tudo bem se você consegue viver com isso, rs. Estes *endpoints* não estão errados, a nível de código, e irão funcionar normalmente sem lançamento de exceções ou algo do tipo. Porém, eles não respeitam a questão semântica do estilo arquitetural, visto que, no primeiro caso, um verbo **GET** está sendo usado para deleção, e no segundo, **PUT** usado para criação.

## Dica

Para aprimorar a habilidade de criação de *endpoints* semânticos, basta imaginar sua *api* como uma estrutura de diretórios.

Considerando a entidade **Usuario**, imagine que você possui uma pasta chamada `Usuarios`, criada dentro do diretório `Sistema`. Dentro desta pasta, existem várias pastas, uma para cada usuário do sistema, onde cada nome de pasta seja equivalente ao *Id* do respectivo usuário. Em cada pasta de usuário, estaria um arquivo de texto com os dados do mesmo.

```sh
 _ Usuarios
   |
   |_ 1
   |  |_ usuario_1.txt
   |
   |_ 2
   |  |_ usuario_2.txt
   |
   |_ 3
      |_ usuario_3.txt
```

Navegando pelo gerenciador de arquivos do seu sistema operacional, abrir a pasta de `Usuarios` lhe exibirá a lista de *Id*s de usuários do sistema. Consequentemente, abrir a pasta de um usuário mostrará suas informações. O "endereço" de navegação entre arquivos seria:

- `/Sistema`, para mostrar a pasta de usuários;
- `/Usuarios`, para exibir os Ids;
- `/Usuarios/1`, para ler informações de um usuário.

Caso queira excluir um usuário, basta excluir a pasta do seu *Id*; Para atualizar, incluir um novo arquivo na sua pasta de *Id*; e para criar, basta adicionar uma nova pasta dentro do diretório `Usuarios`.

Agora, basta utilizar a mesma ideia para criar *endpoints* para todos os verbos **HTTP**. Exemplo:

| **Verbo** | **Recurso** | **Descricao** |
| --------  | ----------- | ------------- |
| **GET**   | `/usuarios` | Retorna a lista de usuários do sistema |
| **GET**   | `/usuarios/:id` | Retorna dados do usuário pelo seu Id informado |
| **POST**  | `/usuarios` | Envia um novo usuário para ser inserido no sistema, no corpo da requisição |
| **PUT**   | `/usuarios/:id` | Envia dados para atualização do usuário, de acordo com seu *Id* informado |
| **DELETE** | `/usuarios/:id` | Exclui do sistema o usuário pelo seu Id informado |

## Conclusão

A discussão sobre **REST** vs **RESTful** na realidade é uma discussão desnecessária. Cabe ao time decidir se haverá regras tão formais sobre a criação de *apis* ou mais maleáveis. O importante é manter a consistência através do código para evitar falhas de interpretação e divergências entre os membros.

## Referência

- [Roy Fielding Paper - Chapter 5](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
