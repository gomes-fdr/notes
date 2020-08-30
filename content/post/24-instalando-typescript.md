---
title: "Instalando Typescript"
date: 2020-08-29T20:48:40-03:00
slug: "instalando-typescript"
draft: false
tags: ["project"]
---

> TypeScript is a typed superset of JavaScript that compiles to plain JavaScript. In this guide we will learn how to integrate TypeScript with webpack.
> [fonte](https://webpack.js.org/guides/typescript/)

Uma da *stacks* que usamos na empresa onde trabalho é o typeScript, esse foi um dos principais motivos de adiciona-la no meu projeto de estudo. Tenho estudado mais a respeito e para quem não vem do mundo javascript, como eu, o *ts* como a galera chama é uma mão na roda.

Então qual é a idéia principal? Tornar-se produtivo no desenvolvimento javascript e isso também implica em cometer menos erros durante o processo de codar javascript. É aqui que *typescript* parece ser um excelente auxiliar, ele ajuda a evitar erros comuns para caras que vem de linguagens compiladas e que passaram pela checagem de um compilador.

Outra face do *typescript* que achei bacana é de aproximar conceitualmente essa linguagem a outras mais conhecidas por mim, como o C++. Essa aproximação acontece na tipagem e na orientação a objetos.

## Habilitando isso no webpack

No terminal: 

    npm install --save-dev typescript ts-loader
    npm install --save-dev @types/lodash

Criar um arquivo de configuração do webpack, `webpack.config.js`:

    const path = require('path');

    module.exports = {
    entry: './src/index.ts',
    devtool: 'inline-source-map',
    module: {
        rules: [
        {
            test: /\.tsx?$/,
            use: 'ts-loader',
            exclude: /node_modules/,
        },
        ],
    },
    resolve: {
        extensions: [ '.tsx', '.ts', '.js' ],
    },
    output: {
        filename: 'bundle.js',
        path: path.resolve(__dirname, 'dist'),
    },
    };

Precisamos criar um arquivo de configuração do typescript, `tsconfig.json`:

    {
        "compilerOptions": {
            "outDir": "./dist/",
            "sourceMap": true,
            "noImplicitAny": true,
            "module": "es6",
            "target": "es5",
            "jsx": "react",
            "allowJs": true
        }
    }

Alterar o arquivo `index.html`

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Getting Started</title>
    </head>
    <body>
        <script src="bundle.js"></script>
    </body>
    </html>

E por fim, compilar nosso arquivo ts para js

    npx webpack

Pronto, agora podemos codar em typescript sem complicações.



