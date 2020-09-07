---
title: "Vuejs Ecosystem"
date: 2020-09-07T17:10:39-03:00
slug: "vuejs-ecosystem"
draft: false
tags: ["project"]
---
No último post eu adicionei ao projeto, o *poder* de codar em *typescript*. Bom agora quando cheguei na parte de adicionar a capacidade de usar o framework [Vuejs](https://vuejs.org/) eu me deparei com uma ferramenta chamada vue-cli.

## Reestruturando as idéias

O vue-cli é uma espécie de *wrapper* para uso do webpack, atrávés dele podemos:

* Iniciar um projeto vuejs, criando um boilerplate do projeto
* Adicionar o uso de typescript para codarmos nosso app em vuejs usando essa linguagem
* Adicionar um framework de frontend

### Sobre os frameworks de frontend

Fiz alguns testes e eis minhas considerações:

* [Bootstrap-vue](https://bootstrap-vue.org/): Não consegui fazer funcionar com o typescript
* [Vuefy](https://vuetifyjs.com/en/): Não consegui fazer funcionar
* [Buefy](https://buefy.org/): Tudo funcionou out-of-the-box!

Por motivos óbvios escolhi o Buefy.

## Processo de instalação

Confesso que ficava com um pé atrás com essas ferramentas que promentem fazer e configurar tudo para o desenvolvedor, mas o vue-cli é uma ferramenta bem honesta, nota para a versão gráfica chamada *vue ui* - bem legal também.

Esta foi a sequência de criação da UI web usando `vuejs+typescript+buefy`

    # Para instalar o vue-cli global
    npm install --global @vue/cli

    # Para criar nosso projeto
    #  Durante o setup escolhi a opção de configurar manualmente
    #  Nesta opção podemos, instalar o typescript, escolher a versão do vuejs, linter, etc...
    vue create tracker-ui
    cd tracker-ui

    # Para adicionar o framework buefy
    vue add buefy

Agora chegamos no ponto que todo deve gosta, vamos codar o front-end do nosso sistema de tracker.
