---
title: "4 dicas Para Aprender Golang"
date: 2020-07-11T16:18:52-03:00
slug: "4-dicas-para-aprender-golang"
draft: false
---

## Chegando na Golândia: A jornada de um desenvolvedor sênior.

*Tradução livre do artigo de [Phil Estes](https://opensource.com/users/estesp) na [opensource.com](https://opensource.com/article/18/11/learning-golang).*

No verão de 2014...
> IBM: "Nós gostaríamos de consertar este problema no Docker."

> Me: "OK."

> IBM: "Comece contribuindo e se envolva com o projeto."

> Me: "OK." (Voz interna): "Isto é escrito en Go. Como isso é...?!" (Google) "Hum, uma linguagem de programação. Eu tenho aprendido algumas delas ao longo da minha carreira. Não pode ser difícil."

Minhas aulas inicias de programação na faculdade foram ensinadas usando VAX assembler. Em estruturas de dados, nós usávamos Pascal - carregado usando disquetes em um velho PC da biblioteca do centro de computação. Na de graduação, eu tinha um professor que amava mostrar todos os exemplos em ADA. Eu aprendi um pouco de C brincando com o código fonte de vários utilitários Unix em estações de trabalho da Sun. Na IBM nós usávamos C - e um pouco de assembler - para os fontes do OS/2, e bastante funcionalidades da orientação a objetos do C++ para um projeto em conjunto com a Apple. Eu aprendi shell script logo depois, começando com csh, mas trocando para Bash depois que conheci o Linux no meu dos anos 90. Eu verdadeiramente aprendi m4(é discutível se é uma linguagem para criação de macros ou uma linguagem de programação) enquanto eu trabalhava no código do compilador JIT na JVM customizada da IBM no final dos anos 90.

Passaram-se 20 anos...Eu nunca fiquei nervoso por aprender uma nova linguagem de programação. Mas Go me fez sentir diferente. Eu estava para contribuir de forma pública, no github, visível para qualquer um interessado o suficiente para olhar! Eu não gostaria de ser uma chacota, o novato em Go com mais de 40 anos de idade, desenvolvedor sênior! Todos nós sabemos que o orgulho de um programador não gosta de ser machucado, não importa o seu nível de experiência.

Minhas investigações iniciais revelaram que Go parecia mais comprometida com sua "idiomática" do que outras linguagens. Isso não era somente sobre compilar o código; Eu precisava ser capaz de escrever código da "Maneira Go".

Agora que já tinha 4 anos e várias requisições de alterações na minha jornada de aprendizado de Go, eu não posso dizer que sou um *expert*, mas eu me sinto muito mais confortável para contribuir e escrever código em Go do que em 2014. Então, como você ensina caras das antigas novos truques - ou pelo menos uma nova linguagem de programação? Aqui vão quatro passos que foram valiosos na minha jornada na Golândia.

## 1. Não pule os fundamentos

Embora você possa se dar bem copiando código e catando soluções prontas durante seu aprendizado(quem tem tempo para ler manuais?!), Go tem uma especificação da linguagem muito boa e que foi escrita para ser lida e entendida, mesmo se você não tem uma formação em teoria de compiladores. Dito isso, Go tomou algumas decisões únicas sobre como a ordem de *parameter:type* são construídas e existem funcionalidades interessantes da linguagem como *channels* e *goroutines*, isso é importante para entendermos estes novos conceitos. Lendo estes documentos contidos em [*Effective Go*](https://golang.org/doc/effective_go.html), outra grande fonte dos criadores da Golang, dará a você uma grande acelerada no entendimento para usa-la de maneira efetiva e apropriada.

## 2. Aprenda com os melhores

Existem muitas fontes de muito valor para fuçar, aumentar e elevar o seu conhecimento em Go para um próximo nível. Todas as palestras recentes da [*GopherCon*](https://www.gophercon.com/) podem ser encontradas *online*, como esta exaustiva lista da [*GopherCon US* de 2018](https://tqdev.com/2018-gophercon-2018-videos-online). Diversas palestras de diferentes assuntos e níveis, mas é fácil encontrar algo do seu interesse assistindo as palestras do [Francesc Campoy](https://twitter.com/francesc) criador de uma série de vídeos sobre Golang chamada [*JustForFunc*](https://www.youtube.com/channel/UC_BzFbxG2za3bp5NRRRXJSw) que tem um crescente numero de episódios para aumentar seu conhecimento e entendimento de Go. Uma pesquisa rápida sobre "Golang" revela inumeros outros vídeos e recursos *online* para aqueles que querem aprender mais.

Quer ver um pouco de código? Muito dos mais populares projetos baseados na nuvem no Github são escritos em Go: Docker/Moby, Kubernetes, Istio, containerd, CoreDNS, e muito outros. Puristas da linguagem podem classificar alguns projetos melhores que outros em relação a linguagem, mas esses são bons pontos de partida para ver como grandes projetos estão usando Go em projetos de grande atividade.

## 3. Use boas ferramentas

Você vai aprender rápido o valor do gofmt. Um dos aspectos mais bonitos de Go é que não existe discução sobre formatação de código fonte - gofmt faz parte da *runtime* da linguagem e formata código Go de acordo com um conjunto estável e bem compreendido de regras da linguagem. Eu não conheço nenhum projeto baseado em Golang que não utilize gofmt em *pull requests* como parte de um CI.

Além da ampla e valiosa variedade de ferramentas úteis criadas diretamente no *runtime/SDK*, eu recomendo fortemente usar um editor ou IDE com bom suporte as funcionalidades de Golang. Desde de que eu passei a usar muito mais a linha de comando, eu passei a usar o Vim mais o grande plugin vim-go. Eu também gosto do que a Microsoft tem oferecido com o VS Code, especialmente com os plugins para Go Language.

Procurando uma ferramenta para *debug*? O projeto [*Delve*](https://github.com/derekparker/delve) vem melhorando e amadurecendo e é um forte competidor para fazer o que o gdb faz com binários em Go.

## 4. Se joga e escreva código(em Go)!

Você nunca vai se tornar melhor em escrever código em Go até que você comece a tentar. Encontre um projeto que alguém tenha sinalizado que precisa de ajuda ou contribuição. Se você já usa algum projeto *open-source* escrito em Go, verifique se não existem alguns *bugs* de que um iniciante possa fazer seu primeiro *pull request*. Como muitas coisas na vida, o único jeito real de melhorar é praticando, então vamos lá.

E, como se vê, aparentemente você pode ensinar a um velho desenvolvedor sênior novos truques - ou pelo menos novas linguagens de programação.

*Essa foi uma tradução livre, com o intuito de aprender e ajudar quem está aprendendo Golang e que talvez esteja em uma situação parecida.*
