---
title: Guia básico de comandos do Terminal
date: 2015-03-03 14:00:18
categories: [fundamentals]
tags: [linux]
thumb: terminal.svg
---

Utilizar o **Terminal** de comandos pode parecer uma tarefa complexa, limitada e
intimidadora para usuários não ambientados. Porém, com a enorme adoção de sistemas
operacionais *Linux* por parte de servidores, e *Mac* por desenvolvedores, é
necessário pelo menos um pouco de familiaridade com a ferramenta.

Além disso, a maioria das linguagens e frameworks disponibilizam seus recursos
por meio de *CLI*, que significa *C*ommand *L*ine *I*nterface (*interface de linha
de comando*), mesma prática adotada por ferramentas de outras áreas como banco de
dados e sistemas de controle de versão.

Exemplos:

- nodejs (node e npm)
- emberjs e angular
- php
- ruby
- python
- git e svn
- mysql e postgres

...entre outras.

Ou seja, é praticamente impossível pensar num ambiente de desenvolvimento que não
necessite de nenhuma interação com a linha de comando.

E com o passar do tempo é provável que você adquira mais habilidade e
produtividade utilizando ferramentas do **Terminal**.

## Catálogo

A seguir, um catálogo simplificado para servir como ponto de partida para adaptação
à linha de comando de sistemas baseados em *Unix*, por categoria.

### Navegação

  - `pwd`: imprime o caminho completo do diretório atual.
  - `ls [path]`: lista os arquivos publicos informados no parâmetro `path`.
  - `cd [path]`: navegar para o diretório informado no parâmetro `path`.

### Ajuda

  - `man [command]`: exibe o manual do comando informado no parâmetro `command`.
  - `[command] --help` ou `[command] -h`: geralmente, ferramentas da linha de comando
    irão exibir um menu de opções disponíveis e informações de utilização do comando
    informado no parâmetro `command`.

### Manipulação de arquivos

  - `cp [source] [destination]`: copiar o arquivo informado no parâmetro `source`
    para o caminho no parâmetro `destination`.
  - `mv [source] [destination]`: mover arquivo ou pasta do parâmetro `source` para
    o caminho informado em `destination`, ou renomear caso o destino seja o mesmo
    diretório.
  - `touch [filename]`: cria um arquivo com o nome informado no parâmetro `filename`.
  - `mkdir [fullpath]`: cria um diretório com o caminho completo informado no parâmetro `fullpath`.
  - `rm [filename]`: excluir o arquivo informado no parâmetro `filename`.
  - `rm -r [path]`: exclui um diretório informado no parâmetro `path`.
  - `ln -s [source] [destination]`: cria um link simbólico entre o arquivo informado
    no parâmetro `source` e o destino informado no `destination`.

### Visualização de arquivos

  - `echo [text]`: imprime o texto informado no parâmetro `text` no terminal.
  - `echo $[varname]`: exibe o conteúdo presente na variável informada no parâmetro `varname`.
  - `cat [filename]`: imprime o conteúdo presente no arquivo informado no parâmetro `filename`.
  - `head [filename]`: imprime as dez primeiras linhas do arquivo informado no parâmetro `filename`.
  - `tail [filename]`: imprime as dez últimas linhas do arquivo informado no parâmetro `filename`.
  - `grep [pattern] [filename]`: imprime as linhas do arquivo informado no parâmetro `filename` que satisfazem o padrão (*Regex*) informado no parâmetro `pattern`.

### Administração

  - `sudo [command]`: executa o comando informado no parâmetro `command` como super usuário.
  - `[command1] && [command2]`: o operador `&&` permite que vários comandos sejam executados em sequência.
  - `[command] &`: executa o comando informado no parâmetro `command` em segundo plano.
  - `bash [script.sh]`: utiliza o *bash* para executar o script informado no parâmetro `script.sh`.
  - `[command1] | [command2]`: redireciona a saída do comando `command1` para a entrada do
    comando `command2`.
  - `[command] > [filename]`: redireciona a saída do comando `command1` para um
    arquivo criado com o nome informado em `filename`.
  - `[command] >> [filename]`: adiciona a saída do comando `command1` no final do
    arquivo informado no parâmetro `filename`.

### Processos

  - `ps`: exibe uma lista de processos em execução do usuário atual no terminal atual.
  - `ps -e`: exibe todos os processos em execução.
  - `pstree`: exibe a lista de processos em execução, em forma de árvore.
  - `pgrep [name]`: exibe o PID do processo informado no parâmetro `name`.
  - `kill -9 [PID]`: envia o sinal de encerramento para o processo que possui o PID
    informado no parâmetro `PID`.

### Permissões

  - `chmod [code] [filename]`: altera a permissão do arquivo informado em `filename`
    de acordo com o código informado no parâmetro `code`.
  - `chmod +x [filename]`: torna o arquivo `filename` um executável.
  - `chwon [path]`: altera o dono do arquivo ou diretório informado no parâmetro `path`.

### Commando "find"

  - `find .`: procura arquivos e diretórios recursivamente a partir do atual.
  - `find . -name *.png -exec cp '{}' ~/images \;`: copia todos os arquivos PNG para a pasta `~/images`.
  - `find . -name .svn -prune -exec rm -r '{}' \;`: exclui todos os diretórios com nome `.svn`.
  - `find . -type f -exec file '{}' \;`: executa os arquivos.

### Net

  - `ssh user@server`: acessar um servidor via **SSH**.
  - `scp user@host:[remotefile] [localpath]`: Copia o arquivo remoto para uma pasta local.
  - `scp [localfile] user@host:[remotepath]`: Copia um arquivo local para o servidor remoto.
  - `wget [url]`: efetua o download do arquivo informado em `url` a partir da web.
