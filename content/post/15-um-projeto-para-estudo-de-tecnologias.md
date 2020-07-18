---
title: "Um Projeto Para Estudo De Tecnologias"
date: 2020-07-18T18:33:50-03:00
slug: "um-projeto-para-estudo-de-tecnologias"
draft: false
---

A ideia inicial de fazer esse blog, foi para guardar meus projetos e aprendizados para uma analise futura. É muito bom poder olhar para tras e fazer avaliações e balanços.

Tenho estudado diversas tecnologias e escolhi algumas delas para subir um projeto de monitoramento de dispositivo por GPS, esse projeto está divido em três grandes partes. Ele vai me forçar a exercitar diversas habilidades, algumas já tenho e outras preciso adquirir ao longo desta jornada, aqui será meu *backlog* onde vou fazer os registros, tombos e aprendizados.

## O projeto, *draft*

Vamos começar do começo, quais 'entidades' compõem essa versão de draft?

![ER do draft](images/er-track-all.png)

## O frontend

Vou começar por aqui, meu jeito de aprender está muito ligado ao visual. Então começo este trabalho definindo as funções do sistema ao redor das 'telas' que o compõem, esta *stack* será composta de:

  * Páginas html;
  * Comportamento definido por typescript->javascript, usando [Vuejs](https://vuejs.org/);
  * Aparência definida pelo uso do framework [boostrap](https://getbootstrap.com/), devido a larga adoção em produtos comerciais(scss->css);
  * Toda orquestração disso será feita usando [webpack](https://webpack.js.org/).

## O backend

O motor deste sistema será baseada no [Mozilla webthings](https://iot.mozilla.org/) e será construido utilizando:

  * Banco de dados [Postgres](https://www.postgresql.org/);
  * Liguagem de programação [Golang](https://golang.org/);
  * Um serviço de tradução de coordenadas do GPS para uma mapa, ainda não sei como, mas tenho uma idéia [...](https://www.gpsvisualizer.com/)

## O equipamento de rastreio

Estou pensando em usar um GPS comercial acoplado a uma placa controladora com um [tiny85](http://www.interactiondesign.se/wiki/attiny) - ainda com muitos pontos de interrogação aqui.

## A estrutura

Ambos, back e frontend serão aplicações mantidas em containers docker e com deploy na [vultr](https://www.vultr.com/).

## A licensa

~~Eis uma dúvida cruel, é um projeto para meu aprendizado. Tem um bom potencial de mercado, por isso penso em mate-lo sob licensa fechada, ainda não decidi isso, o tempo vai me mostrar a melhor opção.~~

Será opensource, licensa MIT.


