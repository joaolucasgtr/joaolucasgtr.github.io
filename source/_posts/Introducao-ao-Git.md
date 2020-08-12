---
title: Introdução ao Git
date: 2017-06-15 19:34:43
categories: fundamentals
tags: git
thumb: git.svg
---

Como a grande maioria das IDEs e Editores de código já possuem ferramentas gráficas
para gerenciar o versionamento de código, você pode acabar se acomodando à esses
recursos simplificados e não se preocupar em aprender outras maneiras de fazê-lo.

Pode ser que você se veja numa situação onde a sua ferramenta favorita não
esteja disponível (*como numa prova, por exemplo*) ou em outra onde a única ferramenta
disponível para manipulação do sistema operacional seja o tão temido **Terminal**.

Com o domínio absoluto de sistemas operacionais baseados em **Linux** no mercado de
servidores*, é bem provável que você  passe por algo parecido um dia, caso não tenha ainda.

Sendo assim, separei alguns comandos essenciais para o fluxo de trabalho do
dia a dia, agrupados por estágio de utilização para facilitar o entendimento.

*[* fonte](https://hostingtribunal.com/blog/linux-statistics)*

## Configuração

Configurações iniciais:

- `git config --global user.name "John Doe"` - denifir nome global do usuário.
- `git config --global user.email "john_doe@gitlab.com"` - definir email global do usuário.

## Início

Duas maneiras simples para iniciar um repositório **git** local em seu HD:

1. `git clone [url do repositório]` - caso o repositório já exista no servidor
remoto e você quer criar um repositório local exatamente igual ao remoto

2. `git init` - caso você queira transformar a pasta atual em um repositório **git**.
Após a criação, é necessário adicionar o endereço do servidor remoto para que possa
enviar ao servidor as alterações realizadas localmente: `git remote add origin [url do repositório]`.

Feito isso, você já está pronto para utilizar o versionamento de forma local.

## Branches

Após o passo anterior, você automaticamente estará trabalhando na *branch* ***master***,
o que pode não ser considerado uma boa prática por parte da equipe. Geralmente você
vai querer criar uma *branch* para desenvolvimento e, depois das implementações concluídas,
aplicá-las à *branch* ***master*** como conclusão de suas tarefas.

1. `git checkout -b [nome da branch]` - cria a *branch* localmente e já altera
a cópia de trabalho atual.

2. `git push -u` - envia as alterações locais para o servidor remoto, já criando
uma *branch* com o mesmo nome da local.

## Gerenciamento

Comandos utilizados com maior frequência, após as fases de configuração anteriores:

1. `git pull` - sincroniza a versão local com as alterações persistidas no servidor
remoto, enviadas desde a última vez que este comando foi executado. O servidor irá
bloquear suas alterações caso a sua versão local esteja desatualizada.

2. `git add [arquivo ou caminho]` - coloca o arquivo, ou arquivos no caminho, na fila para
o próximo envio de dados ao servidor.

3. `git status` - exibe um relatório de alterações realizadas localmente para conferência.

4. `git reset HEAD [arquivo]` - caso mude de ideia sobre alguma alteração na fila
de envios, utilize este comando para descartar as alterações, removendo assim o
arquivo da fila de envio.

5. `git commit -m "[mensagem]"` - aplica as alterações que estavam na fila até então
no seu servidor local.

6. `git push` - envia para o servidor remoto o pacote de atualizações produzido
localmente na sua máquina, desde a última sincronização.

## Analisando alterações

Para consultar o histórico de alterações, utilize o comando:

- `git log` - abre uma lista descritiva sobre os *commits* realizados até então.
É possível aplicar diversas opções de filtro, como por exemplo:

- `git log --max-count=5` - para exibir os últimos cinco
- `git log --author=John Doe` - para exibir somente *commits* enviados pelo usuário "John Doe"
- `git log --stat` - para ver estatísticas de alteração em cada *commit*
- `git log --since=2.weeks` - *commits* das últimas duas semanas

## .gitignore

Para ignorar alterações em arquivos e pastas de maneira automática no repositório,
é preciso criar o arquivo `.gitignore`, que nada mais é que um arquivo de texto,
sem extensão, onde você irá definir em cada linha o que deverá ser ignorado pelo versionamento.

As definições escritas podem ser arquivos, pastas, subpastas, arquivos de uma determinada
extensão, etc...

## Referência completa:

- [**git**](https://git-scm.com/docs)
- [**.gitignore**](https://git-scm.com/docs/gitignore)
