---
title: "Inicio Do Projeto"
date: 2020-07-26T12:13:29-03:00
slug: "inicio-do-projeto"
tags: ["projeto"]
draft: false
---

Vamos começar do começo, não sei nada de typescript.

Tive uma experiência desagradável com javascript e o ecosistema node, na graduação meu projeto final foi um sistema de automação residencial que usava uma central de controle, uma raspberry PI. Iniciei o projeto utilizando nodejs para criar uma API que controlaria dispositivos via wifi(um IoT posto em prática) - o crescimento da pasta node_modules e a baixa performace do tempo de resposta da API hospedada no pequeno ARM, na época me fizeram optar por outra stack.

Alguns anos depois, novamente precisei me aventurar com javascript, agora no frontend. Como sempre, optei por uma abordagem mais purista, para entender o que rolava e saber como o javascript funciona. Usar javascript vanila não foi uma experiência legal, foi aí que cheguei nos famosos frameworks.

Passei pelo backbone, angular e me senti satisfeito quando vuejs bateu na minha porta. A lógica e o espiríto opensource de cara me chamaram atenção. Iniciei com pequenos testes, sem o uso de ferramentas, como a CLI do vuejs porque não queria utilizar nodejs novamente, consegui uma certa evolução, mas sinto que não tirei o melhor desta experiência.

Chegamos ao meu momento atual, onde quero desenvolver um projeto opensource que vai passar por um frontend web, uma API de controle e acesso e um firmware para acesso a dispositivos com GPS. Hoje me parece óbvio algumas escolhas, então vamos a elas.

## O frontend

Esse projeto de frontend tem a seguinte estrutura:

	├── public
	├── src
	│   ├── app
	│   ├── assets
	│   └── index.js
	├── webpack.common.js
	├── webpack.dev.js
	└── webpack.prod.js

## Próximos passos

Estou organizando as coisas ainda, mas acredito que a sequência/necessidade vai ser mais ou menos essa:

* Uso de nodejs : Vamos usar a versão LTS do nodejs, atualmente é a 12.18.2
* Uso de webpack
* Uso de typescript
* Uso de vuejs
* Uso de bootstrap

Cheguei nesta lista inicial baseado no fato de que grandes soluções e ferramentas usam uma estrutura semelhante.
