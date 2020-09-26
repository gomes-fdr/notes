---
title: "Falando um pouco sobre SOLID"
date: 2020-09-26T15:36:15-03:00
slug: "falando-um-pouco-sobre-SOLID"
tags: ["solid", "opp"]
draft: false
---
Semana passada fui convidado para falar um pouco sobre o que eu sabia sobre S.O.L.I.D. e eu lembrei que que tinha lido um livro a respeito em 2016, lembrava pouco sobre o que tinha lido e percebi que estava na hora de revisitar esse conteúdo.

O livro em questão é o [Orientação a Objetos e SOLID para Ninjas](https://www.casadocodigo.com.br/products/livro-oo-solid?_pos=1&_sid=ab84d16a2&_ss=r) do Maurício Aniche. Excelente conteúdo e didatica de ensino. Seguem algumas notas que resolvi fazer para usar como referência no dia-a-dia.

## [S]ingle responsibility

> Uma classe deve ter apenas um motivo para mudar, o que significa que uma classe deve ter somente um emprego(aplicação).

A filosofia UNIX já falava dele:

> Escreva programas que façam apenas uma coisa, mas que a façam bem feita.

ou

> Faça apenas uma coisa e faça bem.


## [O]pen-closed Principle

> Objetos ou entidades devem ser abertos para extensão, mas fechados para modificação.

Aqui entra uma das coisas que me fizeram revisar a leitura sobre SOLID, este princípio dá a real importância do uso de interfaces. O conceito de interfaces permite a criação de *contratos* no momento de criarmos nossas classe, por exemplo:

	interface ShapeInterface {
		public function area()
	}
	
	class Circle implements ShapeInterface {
		public radius
		
		public function area() {
			...
		}
	}

Essa promessa, ou contrato, obriga quem deseja fazer parte da *turminha* de *shapes* a implementar o método área. Projetar interfaces de forma correta é a parte mais refinada de um sistema orientado a objetos, uma excelente analogia feita no livro, com relação a interfaces é mostrada na figura abaixo.

![puzzle](/images/puzzle.png)

Onde:

  * O quebra-cabeça completo é o nosso sistema;
  * Cada peça do quebra-cabeça é uma classe e tem um domínio próprio;
  * O contorno das nossas peças são as interfaces.
  
Gostei muito dessa analogia, porque mudar interfaces é sempre muito dolorido e deve ser evitado. Afinal nem todo mundo pode estar comprando quebra-cabeças novos a todo momento ;op

O projeto de uma classe e a definição do seu comportamento acaba tendo dois aspectos, o projeto de seus métodos e atributos(aspecto interno). E como essa classe vai se relacionar com as demais classes que compõem um sistema orientado a objetos(aspecto externo). Lembrando que tudo isso faz parte da arquitetura do sistema e cuida de uma parte mais estática do mesmo, a ação, ou o funcionamento do sistema acontece quando as instâncias destas classes passam a trocar mensagens(dados) entre sí.

## [L]iskov substitution principle

>Se **q(x)** é uma propriedade demonstrável dos objetos **x** de tipo **T**. Então **q(y)** deve ser verdadeiro para objetos **y** de tipo **S** onde **S** é um subtipo de **T**.

Diretamente relacionado com o princípio de open-closed, isso é uma das coisas bacanas do SOLID, essa interligação entre os princípios. Onde um acaba influenciando ou reforçando ou outro, fazendo uma leitura prática no que tange orientação a objetos, podemos dizer que:

> As classes derivadas devem ser substituíveis por suas classes bases.

Na comunidade Python se usa muito a seguinte frase(chaga a ser uma parada canônica):

> Se caminha como um pato, grasna como um pato, então deve ser um pato!

A ideia é não verificar se é um pato, verifique o seu *comportamento*. O que é determinado por sua Interface.

![puzzle](/images/duck.jpg)

## [I]nterface segregation principle

> Um cliente nunca deve ser forçado a implementar uma interface que não usa, ou os clientes não devem ser forçados a depender de métodos que não usam.

Podemos usar o exemplo das formas geométricas para entender esse princípio. Não faz sentido, por exemplo, adicionar o método para calculo de volume na nossa interface *ShapeInterface*.

Isso obrigaria a todas as classes que implementam nossa interface a também ter que implementar esse método de volume, o correto seria criar uma interface que leve em consideração objetos com três dimensões. Dessa forma poderíamos usar livremente as duas interfaces e teríamos *contratos* que não invadem os domínios uns dos outros.

## [D]ependency Inversion principle

> As entidades devem depender de abstrações, não de classes concretas. Ele afirma que o módulo de alto nível não deve depender do módulo de baixo nível, mas deve depender de abstrações.

Argumentando de forma mais prática, sempre que precisamos criar uma dependência de outra classe, esta deve ser mais abstrata que a nossa classe atual. Porque esse é um forte indicativo de que a classe que estamos nos tornando dependente irá mudar menos que nossa classe concreta, e classes que mudam menos são por óbvio menos propensas a **BUGS**.

Este foi um apanhado de coisas que lí, ví e ouvi nessas internets da vida. Estes princípios são poucos, mas muito poderosos e aparentemente atemporais, por tanto, sempre vale a pena relembra-los.
