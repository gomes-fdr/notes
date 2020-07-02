---
title: "Golang, sobre strings"
date: 2020-06-14
slug: "golang-sobre-strings"
tags: ["go"]
draft: false
---

Estas são algumas anotações que estou fazendo durante o excelente vídeo curso da [Ellen Körbes](https://www.youtube.com/playlist?list=PLCKpcjBB_VlBsxJ9IseNxFllf-UFEXOdg) - o conteúdo e alguns trechos de código são de lá.

## O tipo string

Uma das coisas que achei muito legal em Go, tudo é utf-8! O código fonte e o tipo string é em utf-8. Bom só quem já usou IDEs como o qtcreator ou o eclipse sabe os tipos de problemas inesperados que podemos ter pelo simples fato de o encode do código fonte poder estar em diversos formatos(lá se vão todas as mensagens para o usuário final com caracteres alienígenas).

## Nota histórica

O mindset para lidar com texto em C, é o seguinte:

    "Strings são uma cadeia de char finalizadas com `0`."
    
Para lidar com ASCII, tudo bem, mas o mundo é muito grande e trabalhar com todos os símbolos que usamos para nos comunicar, usando apenas a tabela ASCII era um ginástica danada.

Seguindo:

    "Um char, em C, são 8 bits."

Observando estas notas históricas, vejo como foi acertada a escolha de utf-8 para lidar com string em Go.

## Como é em Golang

Go criou um alias para `unit32` chamado `rune`, cada `rune` representa um caractere de uma string em Go. Isso impacta diretamente em operações de slice(fatiamento).

    package main

    import (
        "fmt"
    )

    func main() {
        a := "e"
        b := "é"
        c := "香"
        fmt.Printf("%v, %v, %v\n", a, b, c)

        d := []byte(a)
        e := []byte(b)
        f := []byte(c)

        fmt.Printf("%v, %v, %v", d, e, f)
    }

    e, é, 香
    [101], [195 169], [233 166 153]

Observe:

    // caractere | decimal | hexa | binário  | no. byte(s)
               e |     101 |   65 |  1100101 |           1
               é |   50089 |   C3 | 11000011 |
                 |         |   A9 | 10101001 |           2
              香 | 15312537|   E9 | 11101001 |
                               A6 | 10100110 |
                               99 | 10011001 |           3


O primeiro caractere `e` está na tabela ASCII, utf-8 é um superset desta tabela, logo pode representar seus valores com total compatibilidade. Como tal, usa um byte para representa-lo.

O segundo caractere não pode ser representado usando ASCII, logo cai nos casos em que utf-8 passa a nos ajudar de fato, para representar esse caractere, são necesários 2 bytes.

O terceiro caractere também não pode ser representado usando ASCII e está em um range superior da tabela utf-8 e necessita de 3 bytes para representa-lo.

Em resumo, a tabela ASCII pode representar 2^8 valores diferentes(256), já a tabela de utf-8 pode representar 2^32 valores diferentes(4294967296) - sendo que ASCII está contido nesta tabela, acho que até o alfabeto Klingon está lá.

Este exemplo simples mostra muito bem como fica fácil de lidar com strings em Golang, gostaria de deixar o link para uma excelente explicação complementar de como funciona a lógica por trás da codificação utf-8, ele também é um material criado pela [Ellen Körbes](https://medium.com/deffectivego/wtf-utf-8-85bc66a6279).

Recomendo fortemente.
