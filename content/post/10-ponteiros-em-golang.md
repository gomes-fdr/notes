---
title: "Ponteiros em golang"
date: 2020-06-20
slug: "ponteiros-em-golang"
tags: ["go"]
draft: false
---


Em tradução livre, ponteiros são objetos que armazenam endereços de memória [wikipedia](https://en.wikipedia.org/wiki/Pointer_(computer_programming). Um dos temas que podemos tratar quando passamos a utilizar ponteiros, é a maneira como *passamos* informações de uma função para outra.

Por padrão, quando criamos uma função e definimos algum parâmetro, utilizamos a chamada *passagem por referência* onde este parâmetro, solicita para o computador que ele reserve um pouco de memória para armazenar o conteúdo de cada parâmetro declarado(sim parâmetros são como as variáveis dos nossos programas).

    func dobro(a int) int {
        return a*2
    }

No exemplo acima, uma variável do tipo `int` foi criada, para receber o valor da nossa função `dobro`, dentro do nosso programa principal, poderíamos utilizar essa função da seguinte maneira:

    func main() {
        x := 10

        fmt.Println("O valor de x  é: ", x)
        fmt.Println("Seu dobro é: ", dobro(x))
    }

A grosso modo, no exemplo acima, criamos duas variáveis de tamanho de um `int`, como poderíamos fazer a mesma operação sem alocarmos mais uma variável?

## Passagem por referência

Vamos fazer alguns ajustes na função dobro:

    func dobro(a *int) int {
        return *a * 2
    }

Agora a função dobro espera receber um ponteiro, ou se preferir uma referência para uma variável do tipo `int`, na função principal, a utilização da nossa função que trabalha com referências fica assim:

    func main() {
        x := 10

        fmt.Println("O valor de x  é: ", x)
        fmt.Println("Seu dobro é: ", dobro(&x))
    }

Com essa alteração, passamos a reservar apenas uma variável do tipo `int`, uma vez que nossa função apenas *apontou* para o valor da variável x e retornou seu valor multiplicado por 2.

Assim como em C e C++ dá pra fazer muitas coisas legais e perigosas com ponteiros, essa foi uma pequena nota para meu eu do futuro pensar a respeito.

*Importante lembrar que o uso irresponsável de ponteiros pode trazer efeitos indesejados(eu ouvi garbage colector?!)*

Referências: Série de vídeos do [Claudson Oliveira](https://youtu.be/JepHr8egvBI)
