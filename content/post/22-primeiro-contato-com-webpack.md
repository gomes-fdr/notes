---
title: "Primeiro Contato Com Webpack"
date: 2020-08-16T18:03:47-03:00
slug: "primeiro-contato-com-webpack"
draft: false
tags: ["project", "web"]
---

>O presente e o futuro das interfaces de interação com o usuário estão na web.

Está é uma afirmação minha mas, acredito que poucos teriam coragem de refuta-la. 

Dito isso, podemos bater na porta das UIs na web e de suas inúmeras possibilidades.

Já foi tentado simplesmente portar UIs de desktop para web, foram criados toolkits pensando em resolver esse problema, lembram dos applets Java? No final das contas esse problema foi resolvido usando o bom e velho html + javascript + css.

Com essa combinação foi possível criar soluções incríveis que usamos diariamente, mas isso tem um custo, o aumento da complexidade.

## Como organizar e fazer uma boa cola?

Equilibrar essas três pernas e conseguir um bom balanço(produtividade + robustez) - exige um esfoço gigante, acredite eu já tentei. Mas que dificuldade é essa afinal?

Existem milhares se não milhões de frameworks e bibliotecas de javascript e css por ai, cada uma com seus prós e contras, agora integrar isso em um projeto e manter a sanidade não é uma tarefa simples. Por esse motivo foram criadas ferramentas para fazer essa cola de uma maneira mais simples, a web funciona do mesmo jeito a décadas, de forma super simplificada:

> O browser faz uma requisição a um servidor(outro computador), este devolve um resultado, este resutado vem encapsulado de tal maneira que o browser sabe como descascar essa cebola e exibir essa resposta de forma apropriada.

Mas como todo esse conteúdo foi criado?

Eis a estrutura de projeto que o [webpack](https://webpack.js.org/) sugere:

    .
    ├── dist
    │   ├── index.html
    │   └── main.js
    ├── package.json
    ├── package-lock.json
    └── src
        └── index.js

Onde a pasta `dist` guarda o *build* do nosso projeto, desta forma trabalhamos a lógica de funcionamento do nosso *frontend* nos arquivos contidos na pasta *src*.

O arquivo `index.html` é o container do nosso app, veja o conteúdo:

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Getting Started</title>
    </head>
    <body>
        <script src="main.js"></script>
    </body>
    </html>

Estes foram os comandos utilizados para fazer essa *mágica* acontecer:

    npm init -y
    npm install webpack webpack-cli --save-dev
    npm install --save lodash
    npx webpack

Destes, apenas o último nos interessa no momento, ele que faz o *build* e cria o arquivo `main.js` concatenando toda nossa app contida na pasta src em um ÚNICO arquivo, acertando os caminhos de busca de `assets` e bibliotecas utilizados.Essa é a mágica dos *bundlers*.

Este exemplo segue as orientações contidas neste artigo introdutório do site do [webpack](https://webpack.js.org/guides/getting-started/).

Na sequência vou adicionar novos poderes ao projeto com a ajuda do webpack, vamos adicionar a capacidade de utilizar [typescript](https://www.typescriptlang.org/) para codar nosso front.