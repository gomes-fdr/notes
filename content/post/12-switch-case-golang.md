---
title: "Switch case em Golang"
date: 2020-07-04
slug: "switch-case-golang"
tags: ["go"]
draft: false
---

O uso desse condicional evita uma sequência de `if/else` que por vezes podem tornar dificil a leitura do código.

## Nota histórica

> Em `C` o `swicth/case` aceitava somente statements do tipo `int` ou `char`.

É partindo disso que quero explorar o quando esse condicional pode ser poderoso em golang, a estrutura básica é a seguinte:

	switch statement; expression {
	case expression1:
	     //Dosomething
	case expression2:
	     //Dosomething
	default:
	     //Dosomething
	}

> statement:  The smallest standalone element of an imperative programming language [wikipedia](https://en.wikipedia.org/wiki/Statement_(computer_science)) - O menor elemento unitário de uma linguagem de programação imperativa(tradução livre).

> expression: An instruction to execute something that will return a value [wikipedia](https://en.wikipedia.org/wiki/Expression_(computer_science)) - Uma instrução que executa algo e retorna um valor(tradução livre).

## Pontos importantes

Note que pode haver uma combinação de possibilidades aqui, no caso, quatro.

  * Ambos, *statement* e *expression* presente.
  * Apenas *statement* presente.
  * Apenas *expression* presente.
  * Nenhum dos dois presentes(wtf!?).

A ordem de execução e comparação é:
  * De cima para baixo.
  * Da esquerda para direita.

Se usamos *statement* é obrigatório o uso do ';'.

~~Diferente do `C` o uso do `break` não é necessário, embora torne a leitura mais legível(na minha modesta opinião).~~

Como no `C` o `default` é opcional.

Expressões são separados por vírgula.

Dois *case blocks* não podem ter uma constante de mesmo valor(erro de compilação).

## A instrução *fallthrough*

Mais uma novidade, essa instrução deve ser usada dentro *case blocks*, ela tranfere o controle para o próximo *case block*, mesmo que o valor do bloco corrente tenha 'casado' com a expressão a ser avaliada.

	i := 45
	switch {
	case i < 10:
	  fmt.Println("i is less than 10")
	  fallthrough
	case i < 50:
	  fmt.Println("i is less than 50")
	  fallthrough
	case i < 100:
	  fmt.Println("i is less than 100")
	}

	$ i is less than 50
	$ i is less than 100


*Fallthrough* precisa estar nos *statements* finais do *switch*, se não o compilador **grita!**.

## Descobrindo o 'tipo' do dado

Essa é uma instrução válida e muito usada:

	var t interface{} = 10

	switch t.(type) {
	case string:
	  fmt.Println("Type: string")
	case int:
	  fmt.Println("Type: int")
	default:
	  fmt.Printf("Unknown Type %T", t)
	}

	$ Type: int

Estas foram minha anotações sobre `switch/case` em golang, esta é a um tradução livre e adaptada do artigo de mesmo tema do excelente site [Go by Example](https://golangbyexample.com/switch-statement-golang/). 
