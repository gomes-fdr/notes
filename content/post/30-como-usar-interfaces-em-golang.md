---
title: "Como Usar Interfaces Em Golang"
date: 2020-10-04T18:21:27-03:00
slug: "como-usar-interfaces-em-golang"
draft: false
tags: ["golang", "go"]
---

> Golang tem algumas particularidades e escolhas de arquitetura bem interessantes, o uso de interfaces é um destes casos. Encontrei esse artigo e me ajudou a entender um pouco melhor seu funcionamento, espero que seja útil para mais alguém. Está é uma tradução livre com algumas notas pessoais do artigo de [Jordan Orelli](https://jordanorelli.com/post/32665860244/how-to-use-interfaces-in-go)

Antes de começar a programar em Golang, eu fazia a maior parte do meu trabalho usando Python. Como programador Python, descobri que aprender a usar interfaces em Golang era extremamente difícil. Ou seja, o básico era fácil e eu sabia como usar as interfaces da biblioteca padrão, mas foi necessário alguma prática antes de saber como projetar minhas próprias interfaces. Neste artigo, discutirei o sistema de tipos de Golang em um esforço para explicar como usar interfaces de maneira eficaz.

## Introdução às interfaces

Então, o que é uma interface? Uma interface são duas coisas: é um conjunto de métodos, mas também é um tipo. Vamos nos concentrar primeiro no aspecto do conjunto de métodos das interfaces.

Normalmente, somos apresentados às interfaces com alguns exemplos. Vamos usar o exemplo de escrever algum aplicativo onde você está definindo o tipo de dados  Animal, porque essa é uma situação totalmente realista que acontece o tempo todo. O tipo Animal será uma interface e definiremos um Animal como sendo  **qualquer coisa que possa falar** . Este é um conceito central no sistema de tipos de Golang; em vez de projetar nossas abstrações em termos de que tipo de dados nossos tipos podem conter, projetamos nossas abstrações em termos de quais ações nossos tipos podem executar.

Começamos definindo nossa interface Animal:

	type Animal interface {
	    Speak() string
	}

Muito simples: Definimos Animal como sendo qualquer tipo que tenha um método denominado *Speak*. O método *Speak* não aceita argumentos e retorna uma string. Qualquer tipo que defina esse método satisfaz a interface Animal. Não há palavra-chave *implements* em Golang; Se um tipo satisfaz ou não uma interface é determinado automaticamente. Vamos criar alguns tipos que satisfaçam esta interface:

	type Dog struct {
	}

	func (d Dog) Speak() string {
	    return "Woof!"
	}

	type Cat struct {
	}

	func (c Cat) Speak() string {
	    return "Meow!"
	}

	type Llama struct {
	}

	func (l Llama) Speak() string {
	    return "?????"
	}

	type JavaProgrammer struct {
	}

	func (j JavaProgrammer) Speak() string {
	    return "Design patterns!"
	}

Agora temos quatro tipos diferentes de animais: Um cachorro, um gato, um lhama e um programador Java. Em nossa função *main()*, podemos criar um *slice* de *Animals* e colocar um de cada tipo nesse *slice* e ver o que cada animal diz.

Vamos fazer isso agora:

	func main() {
	    animals := []Animal{Dog{}, Cat{}, Llama{}, JavaProgrammer{}}
	    for _, animal := range animals {
		    fmt.Println(animal.Speak())
	    }
	}

Ótimo, agora você sabe usar interfaces e não preciso mais falar sobre elas, certo? Bem, não, realmente não. Vejamos algumas coisas que não são muito óbvias para o gopher iniciante.

## O tipo interface{}

O tipo *interface{}*, uma interface vazia, é fonte de muita confusão. O tipo *interface{}* é a interface que não possui métodos. Como não há palavra-chave *implements*, todos os tipos implementam pelo menos zero métodos, e o satisfazer a uma interface é feito automaticamente, todos os tipos atendem à interface vazia. Isso significa que, se você escrever uma função que tenha um valor de *interface{}* como parâmetro, poderá fornecer a essa função qualquer valor.

Então, esta função:

	func DoSomething(v interface{}) {
	   // ...
	}

Aceitará qualquer parâmetro que seja.

> Aqui a galera de *Rust* pira! Realmente, devemos ter muito cuidado com tipos sem tipos(minha nota pessoal).

É aqui que fica confuso: dentro da função *DoSomething*, qual é o tipo de v? *Gophers* iniciantes são levados a acreditar que “v é de qualquer tipo”, mas isso está errado, v não é de nenhum tipo; é do tipo *interface{}*. Espere o que? Ao passar um valor para a função *DoSomething*, em tempo de execução Go executará uma conversão de tipo (se necessário) e converterá o valor em um valor de *interface{}*. Todos os valores têm exatamente um tipo em tempo de execução e v é um tipo estático de *interface{}*.

Isso deve deixar você se perguntando: Ok, então se uma conversão está ocorrendo, o que está realmente sendo passado para uma função que assume um valor de *interface{}* (ou, o que está realmente armazenado em uma *Slice* []Animal)? Um valor de interface é constituído de duas *words* de dados; Uma *word* é usada para apontar para uma tabela de métodos para o tipo subjacente do valor e a outra word é usada para apontar para os dados reais mantidos por esse valor. Eu não quero falar sobre isso indefinidamente. Se você entender que um valor de interface tem duas palavras de largura e contém um ponteiro para os dados subjacentes, isso normalmente é o suficiente para evitar armadilhas comuns. Se você está curioso para saber mais sobre a implementação de interfaces, acho que a descrição de interfaces de [Russ Cox](https://research.swtch.com/interfaces) é muito, muito útil.

> Lembrando que uma *word* varia em função da arquitetura do SO: 8, 16, 32 e 64 bits por exemplo(minha nota pessoal).

Em nosso exemplo anterior, quando construímos um *slice* de Animais, não precisamos dizer algo oneroso como *Animal(Dog{})* para colocar um valor do tipo *Dog* no *slice* de valores de Animais, porque a conversão foi feita para nós automaticamente. Dentro do *slice* dos animais, cada elemento é do tipo Animal, mas nossos diferentes valores têm diferentes tipos subjacentes.

Então, por que isso importa? Bem, entender como as interfaces são representadas na memória torna algumas coisas potencialmente confusas muito óbvias. Por exemplo, a pergunta "posso converter um []T em uma []interface{}" é fácil de responder, uma vez que você entenda como as interfaces são representadas na memória. Aqui está um exemplo de código que está quebrado e representa um mal-entendido comum do tipo *interface{}*:

	package main

	import (
	    "fmt"
	)

	func PrintAll(vals []interface{}) {
	    for _, val := range vals {
		fmt.Println(val)
	    }
	}

	func main() {
	    names := []string{"stanley", "david", "oscar"}
	    PrintAll(names)
	}

	$: cannot use names (type []string) as type []interface {} in argument to PrintAll

Ao executar isso, você pode ver que encontramos um erro. Se quisermos realmente fazer isso funcionar, teríamos que converter a *[]string* em uma *[]interface{}*:

	package main

	import (
	    "fmt"
	)

	func PrintAll(vals []interface{}) {
	    for _, val := range vals {
		fmt.Println(val)
	    }
	}

	func main() {
	    names := []string{"stanley", "david", "oscar"}
	    vals := make([]interface{}, len(names))
	    for i, v := range names {
		vals[i] = v
	    }
	    PrintAll(vals)
	}

	$: stanley
	   david
	   oscar

Isso é muito feio, mas *c'est la vie*. Nem tudo é perfeito (na realidade, isso não aparece com muita frequência, porque a *[]interface{}* acaba sendo menos útil do que você esperava inicialmente).

## Ponteiros e Interfaces

Outra sutileza das interfaces é que uma definição de interface não prescreve se um implementador deve implementar a interface usando um receptor de ponteiro ou um receptor de valor. Quando você recebe um valor de interface, não há garantia se o tipo subjacente é ou não um ponteiro. Em nosso exemplo anterior, definimos todos os nossos métodos em receptores de valor e colocamos os valores associados no *slice* Animal. Vamos mudar isso e fazer com que o método do gato *Speak()* receba um ponteiro:

	func (c *Cat) Speak() string {
	    return "Meow!"
	}

	func main() {
		animals := []Animal{Dog{}, Cat{}, Llama{}, JavaProgrammer{}}
		for _, animal := range animals {
			fmt.Println(animal.Speak())
		}
	}

	$: cannot use Cat literal (type Cat) as type Animal in slice literal:
	Cat does not implement Animal (Speak method has pointer receiver)

Essa mensagem de erro é um pouco confusa no começo, para ser honesto. O que está dizendo não é que a interface Animal exige que você defina seu método como um receptor de ponteiro, mas que você tentou converter uma estrutura *Cat* em um valor de interface Animal, mas apenas `*Cat` satisfaz essa interface. Você pode corrigir esse bug passando um ponteiro `*Cat` para o *slice* Animal em vez de um valor *Cat*, usando *new(Cat)* em vez de *Cat{}* (você também pode dizer *&Cat{}*, eu simplesmente prefiro *new(Cat)*):

	animals := []Animal{Dog{}, new(Cat), Llama{}, JavaProgrammer{}}
	
	$: Woof!
	   Meow!
	   ?????
	   Design patterns!

Vamos na direção oposta: vamos passar um ponteiro de `*Dog` em vez de um valor de *Dog*, mas desta vez não mudaremos a definição do método Speak do tipo Dog:

	animals := []Animal{new(Dog), new(Cat), Llama{}, JavaProgrammer{}}

Isso também funciona, mas reconheço uma diferença sutil: não precisamos alterar o tipo de receptor do método Speak. Isso funciona porque um tipo de ponteiro pode acessar os métodos de seu tipo de valor associado, mas não vice-versa. Ou seja, um valor `*Dog` pode utilizar o método *Speak* definido em *Dog*, mas, como vimos anteriormente, um valor *Cat* não pode acessar o método *Speak* definido em `*Cat`.

Isso pode parecer enigmático, mas faz sentido quando você se lembra do seguinte: **tudo em Go é passado por valor.** Cada vez que você chama uma função, os dados que você está passando para ela são copiados. No caso de um método com receptor de valor, o valor é copiado ao chamar o método. Isso é um pouco mais óbvio quando você entende que um método com a seguinte assinatura:

	func (t T)MyMethod(s string) {
	    // ...
	}

É uma função do tipo `func(T, string)`; receptores de método são passados para a função por valor, assim como qualquer outro parâmetro.

Quaisquer alterações no receptor feitas dentro de um método definido em um tipo de valor (por exemplo, `func(d Dog) Speak () {...}`) não serão vistas pelo chamador porque o chamador está definindo um valor Dog completamente separado. Como tudo é passado por valor, deve ser óbvio por que um método `*Cat` não pode ser usado por um valor `Cat`; Qualquer valor *Cat* pode ter qualquer número de ponteiros `*Cat` que apontem para ele. Se tentarmos chamar um método `*Cat` usando um valor Cat, nunca tivemos um ponteiro `*Cat` para começar. Por outro lado, se tivermos um método do tipo *Dog* e tivermos um ponteiro `*Dog`, saberemos exatamente qual valor Dog usar ao chamar esse método, porque o ponteiro `*Dog` aponta para exatamente um valor *Dog*; Em tempo de execução Go cancelará a referência do ponteiro para seu valor *Dog* associado sempre que necessário. Ou seja, dado um valor `*Dog d` e um método do tipo *Speak Dog*, podemos apenas dizer *d.Speak()*; Não precisamos dizer algo como *d->Speak()* como faríamos em outras línguagens de programação.

> O artigo original segue com alguns exemplos de implementações que optei por não traduzir aqui.

> Gostei bastante da maneira como o autor demonstrou o funcionamento e uso de interfaces em Golang, seguimos na caminhada...























