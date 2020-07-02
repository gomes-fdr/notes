---
title: "Conhecendo deno, a node killer?!"
date: 2020-05-22
slug: "conhecendo-deno-a-node-killer"
tags: ["javascript"]
draft: false
---

Em maio tivemos o lançamento da nova runtime de js, o [deno](https://deno.land/). Vamos brincar um pouco.

## Instalação

É muito fácil instalar o deno, o site explica de forma bem simplificada como fazer, mas vamos fazer um pouco diferente, utilizando o [ASDF](https://asdf-vm.com):

	asdf list all deno      # Para ver todoas as versões disponíveis
	asdf install deno 1.0.1 # Instalação da versão mais atual nesta época
	asdf global deno 1.0.1  # Ativando o uso da versão instalada

Pronto!

## Primeiro teste

Vamos ver se tudo está ok:

	deno -V
	deno 1.0.1

Mãos no código:

	deno
	Deno 1.0.1
	exit using ctrl+d or close()
	> 
	let hello = "olá deno"
	console.log(hello)
	olá deno
	undefined

## Segundo teste, usando um arquivo

	deno run hello.ts # Sim, typescript é builtin
	Compile file:///hello.ts
	Olá deno

## Nota final

Ainda estou conhecendo mais a respeito do uso de runtimes javascript/typescript, fazem parte da stack que usamos no meu trabalho, acho interessante conhecer as possibildades tanto do chamado padrão de mercado, quanto de opções recém chegadas.
