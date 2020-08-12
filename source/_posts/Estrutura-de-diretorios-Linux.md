---
title: Estrutura de diretórios Linux
date: 2015-08-10 14:17:50
categories: fundamentals
tags: linux
thumb: tux.png
---

O **FHS**, ou (File Hierarchy Standard - *padrão hierárquico de arquivos*), define os principais diretórios para sistemas operacionais Linux ou baseados em *Unix*. O que difere bastante do padrão utilizado pelo *Windows*, onde cada partição do disco rígido recebe uma letra para representá-lo, e pastas do sistema possuem nomes específicos de acordo com seu conteúdo. 

No **FHS**, são utilizadas palavras abreviadas, a maioria contendo três letras, o que pode causar estranheza num primeiro contato e dificultar o entendimento do propósito do diretório. 

Os principais são:

## "/" - A raíz

Tudo no Linux está localizado abaixo do diretório `/`, conhecido como diretório raiz. Mesmo ao montar outras partições, estas estarão abaixo do diretório raiz, diferente do *Windows*, onde outra partição seria montada no caminho `D:` provavelmente.

## /bin - Binários essenciais

Neste diretório estão mantidos todos os binários essenciais para utilização por parte de um usuário. Programas como bash (`sh`), copy (`cp`), VI (`vi`), Process Status (`ps`), entre outros..., estão mantidos aqui. Colocar binários neste diretório garante que o sistema terá esses utilitários mesmo que outros diretórios não sejam montados.

O diretório `/sbin` funciona da mesma maneira, porém contendo utilitários essenciais para administração do sistema. Exemplos: `adduser`, `fdisk`, `iptables`, `reboot`, etc.

## /sbin – Binários de administração

Contém binários de forma similar ao diretório `/bin`, porém os que estão contidos aqui foram criados com a intenção de serem executados por usuários com privilégios de administrador do sistema.

## /boot – Arquivos de Boot

Este diretório contém os arquivos necessários para inicialização do sistema. Por exemplo, os arquivos da ferramenta **GRUB** e os `kernels` estão armazenados aqui.

## /dev – Devices

Distribuições Linux expõem dispositivos como arquivos neste diretório. Embora não sejam realmente arquivos, são exibidos como tal, por exemplo `sda` é exibido como um arquivo mas representa o primeiro drive *SATA* no sistema.

Aqui também são mantidos *pseudo-dispositivos* que não representam de verdade um hardware, como por exemplo o `/dev/null`, que representa um dispositivo especial que não produz dados de saída e nem de entrada, sendo útil para o caso onde é necessário descartar a saída de programas, bastando utilizar o pipe para este dispositivo.

## /etc – Arquivos de configuração

Diretório responsável por manter arquivos de configuração do sistema como um todo. Configurações pessoais de um usuário devem ser mantidos em seu respectivo diretório `/home`.

## /home - Lar

Contém os diretórios base de cada usuário criado no sistema e é responsável por manter os dados deste usuário, além de seu arquivos específicos de configuração. Caso um usuário queira alterar dados na pasta `/home` de outro, é necessário obter privilégios de administrador.

## /lib – Bibliotecas essenciais

Aqui estão mantidas as bibliotecas (*libraries*) essenciais para os programas contidos nos diretórios `/bin` e `/sbin`.

## /lost+found – Arquivos recuperados

Diretório de "achados e perdidos". Caso o sistema quebre, uma checagem de arquivos será realizada no próximo *boot* e quaisquer arquivos corrompidos serão colocados neste diretório para que seja possível analisar e recuperar dados destes arquivos.

## /media – Mídia removível

Responsável por criar sub-diretórios correspondentes à dispositivos de mídia removível conectados ao computador.

## /mnt – Pontos de montagem

Por convenção, é utilizado para montar temporariamente outros discos disponíveis ou partições. Porém, esta operação é possível de ser feita em qualquer outro diretório.

## /opt – Pacotes opcionais

Contém sub-diretórios para pacotes de software opcionais. É comumente utilizada por softwares de terceiros e proprietários.

## /proc – Processos

Contém diretórios virtuais que representam os processos em execução no sistema. Cada diretório é nomeado de acordo com o *ID* do processo e quando o mesmo é encerrado, automaticamente seu diretório irá desaparecer.

## /root – Root home

Este é o diretório `home` do usuário `root`. Como este usuário é diferente dos demais, seu diretório base não fica localizado em `/home/root` mas apenas em `/root`.

## /run – Estado de aplicações

Este diretório fornece um local padrão para as aplicações armazenarem dados sobre seu estado que não podem ser armazenadas no diretório `/tmp`, uma vez que estando lá, os dados poderão ser descartados em algum momento.

## /tmp – Temporários

As aplicações irão armazenar neste diretórios arquivos temporários. Geralmente, estes arquivos serão apagados ao reiniciar o sistema e podem ser deletados ao executar algum utilitário de limpeza do sistema.

## /usr – Binários de usuários

O diretório `/usr` contém aplicações e arquivos utilizados por usuários de forma isolada do resto do sistema. Por exemplo, aplicações que não são essenciais estarão mantidas em `/usr/bin` e não em `/bin`. Comandos que necessitam de privélgio de administrador estarão em `/usr/sbin` e não em `/sbin`. Bibliotecas necessárias para estes programas estarão em `/usr/lib`.

## /var – Arquivos variáveis

O diretório `/var` contém arquivos que podem ser alterados por aplicações, durante o tempo de execução. Um exemplo claro é o sub-diretório `/var/log`, que mantém os *logs* de execução de aplicações e do sistema operacional.

---

Para visualizar a documentação completa, acesse: [FHS-3.0](http://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)
