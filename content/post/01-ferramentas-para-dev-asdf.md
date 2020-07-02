---
title: "Ferramentas Para Dev, ASDF"
date: 2020-05-11
slug: "asdf-uma-ferramenta-para-devs"
tags: ["wiki"]
draft: false
---

Quando começamos a desenvolver software, precisamos montar nossa "caixa de ferramentas" - uma coleção de programas que nos ajudam a ser mais produtivo na criação de software. Se trabalhamos com linguagens interpretadas como javascript, python ou lua - para citar algumas com as quais eu trabalho, é muito comum precisarmos utilizar diferentes versões de interpretadores. É muito complicado e chato fazer isso manualmente, existem diversas ferramentas que resolvem esse tipo de problema dentro do seu escopo, ruby tem o seu gerenciador de ambientes virtuais, python também e por ai vai.
Felizmente alguém pensou em fazer um gerenciador "genérico" para ajudar um grande número de desenvolvedores das mais diversas linguagens, esse projeto chama-se [ASDF](https://asdf-vm.com) e resolve de uma forma muito elegante o problema de convivência de diferentes interpretadores num mesmo computador, vamos ver como fazer a instalação e configuração dele para alguns interpretadores.

## Instalação

Tudo que estou postando aqui foi retirado do site oficial do [ASDF](https://asdf-vm.com) sem dúvida a melhor fonte para funcionalidades mais específicas.

	git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.7.3

## Tonar visível para o seu shell

	echo -e '\n. $HOME/.asdf/asdf.sh' >> ~/.bashrc
	echo -e '\n. $HOME/.asdf/completions/asdf.bash' >> ~/.bashrc

## Como o ASDF funciona?
Ele não armazena cada versão de interpretador no site do projeto, ao invés disso através de receitas é feita a instalação das diferentes versões dos interpretadores que você precisa - na linguagem do ASDF, estas receitas são chamadas de plugins. Então a primeira coisa a ser feita após a instalação do ASDF é a escolha de quais linguagens vamos trabalhar, neste exemplo vou mostrar como fazer a instalação de diferntes versões de Lua.

## Listando os plugins disponíveis
Para saber quais as versões são possíveis de instalar, basta:

	asdf list-all lua
	
Uma saída semelhante a essa será exibida:

	asdf list-all lua
	5.1
	5.2.0
	5.2.1
	5.2.2
	5.2.3
	5.2.4
	5.3.0
	5.3.1
	5.3.2
	5.3.3
	5.3.4
	5.3.5

## Instalando o plugin

	asdf plugin-add lua

## Instalando uma versão

	asdf install lua 5.2.4

## Tornando a versão instalada ativa

	asdf global lua 5.2.4

Aqui cabe um observação importante, como foi dito anteriormente o ASDF não mantém uma cópia dos interpretadores compilados em seu site, ele é apenas um repositório de receitas. Logo essa receita vai baixar os fontes dos respectivos projetos e compila-los - para isso é importante que as dependências necessárias para compilar cada interpretador estejam presentes no seu computador. Em cada repositório de plugin temos uma lista do que é necessário e de como fazer a instalação destas dependências.

## Um exemplo de instalações

	asdf list
	lua
	  5.2.4
	  5.3.5
	python
	  3.7.4
	asdf current
	   lua            5.3.5    (set by /home/fabiano/.tool-versions)
	   python         3.7.4    (set by /home/fabiano/.tool-versions)

Para outros interpretadores basta repetir o processo, facinho.
Finalizamos por aqui esse tutorial, em caso de dúvidas, deixe seu comentário.
