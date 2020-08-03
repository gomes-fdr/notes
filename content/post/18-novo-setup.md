---
title: "Novo Setup"
date: 2020-08-02T19:18:59-03:00
slug: "novo-setup"
tags: ["Linux"]
draft: false
---

Então, aconteceu eu estou neste processo de mudança de SO. Na verdade o SO é o mesmo, Linux, mas eu saí da base Debian para me aventurar no mundo Arch e suas particularidades.

## [Manjaro](https://manjaro.org/)
Uma boa distro, faz a parte pesada do processo(instalação) - Usei duas versões, uma com xfce e outra com gnome. Ambas se mostraram bem estáveis e tudo funcionou *out-of-the-box*.

## [Artix](https://artixlinux.org/)
Sem *systemd*, simples assim. Também é *arch based* e possui versões com *Desktop Enviroment* com um instalador super amigável, instalando o mínimo necessário para usarmos o pc, podemos dizer que é uma instalação básica.

Embora eu tenha achado mais fácil de lidar com Artix do que com o Arch Linux original, tive que fazer um passo extra para que tudo funcionasse corretamente, Qual foi a sequência de pós instalação:

	sudo pacman -Sy archlinux-keyring artix-keyringd
	sudo rm -r /etc/pacman.d/gnupg		
	sudo pacman-key --init		
	sudo pacman-key --populate archlinux artix
	sudo pacman -Scc		
	sudo pacman -Syyu

Todos esses passos foram necessários para reinstalar as chaves(GPG) que são verificadas para a instalação de cada pacote, remoção das chaves antigas e inicialização de um novo chaveiro. Faz mais coisas, mas a grosso modo ajusta o sistema para um correto funcionamento. Distros mais polidas como o Manjaro, provavelmente fazem isso para evitar dores de cabeça para os usuários novatos como eu.

## Toque pessoal
Com tudo funcionando, agora posso instalar o que preciso no meu novo Artix.

* ASDF
	* ASDF -> deno
	* ASDF -> hugo
	* ASDF -> golang
	* ASDF -> nodejs
* Docker
* Git
* Vim
* Tmux
* Oh-my-bash

Tudo pronto para o uso, agora vamos seguir nossa história com Arch Linux Based Distro, sem systemd.

## Um exemplo
Escolhi a opção de Artix que usa o runit como inicializador do SO. Isso trás algumas diferenças quando desejamos subir algum serviço novo, achei muito parecido com o jeito Slackware de ser, por essas e outras que estou curtindo demais a experiência. Segue um pequeno exemplo com a instalação do docker:

	# Para instalar o pacote, também precisamos do script de inicialização
	sudo pacman -S docker docker-runit
	
	# Feita a instalação, basta criar um link simbólico como mostro abaixo.
	sudo ln -s /etc/runit/sv/docker /run/runit/service

Vamos ver como vai ser essa experiência, temos uma *rolling release distro* com um toque de Slackware, parece bom.
