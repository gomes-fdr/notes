---
title: "Aprendendo golang"
date: 2020-06-11
slug: "aprendendo-golang"
tags: ["go"]
draft: false
---

Algumas regras que me ajudam a dar um boost no entendimento de novas tecnolgias:

  * Ler a documentação do projeto [golang](https://golang.org/)
  * Aprender usando testes [TDD](https://en.wikipedia.org/wiki/Test-driven_development)
  * Aprender com exemplos
  * [Vídeos aulas](https://www.youtube.com/playlist?list=PLCKpcjBB_VlBsxJ9IseNxFllf-UFEXOdg) de qualidade, dica do brother [Gusta](https://gushmsilva.keybase.pub/)

Tendo isso como diretiva, vamos começar essa jornada, vamos adionar isso no  arquivo `bash_profile`

	export GOPATH=$HOME/go
	export PATH=$PATH:$GOPATH/bin
	
Depois vamos criar os seguintes diretórios:

	mkdir -p $GOPATH/src $GOPATH/pkg $GOPATH/bin
	
[Referências](https://quii.gitbook.io/learn-go-with-tests/)

## Coisas que gostei até aqui

  * Syntax fácil
  * Instalação de pacotes/depedências
  * Farta documentação, [Godoc](https://godoc.org/)
  * Geração de binários
  * Formatação de código é builtin
  * Suite de testes é builtin
  * Lembra muito C, na sintaxe
  * Lembra muito C, com structs
  * Não usa `;` para finalizar instruções
  * [Short|gopher] operator é muito massa
  * Controle de imports é builtin
  * Controle de uso de variáveis é builtin
  * Fazer build é uma barbada(alguém falou makefile?!)
  * Code-OSS é um editor honesto

## Coisas que vou investigar melhor

  * Lidar com módulos
  * Compilação cruzada
  * Criação de APIs
  * Criação de GUIs
  * Integração com frontend web
