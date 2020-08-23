---
title: "Hardware Wallets"
date: 2020-08-23T18:36:39-03:00
slug: "hardware-wallets"
draft: false
tags: ["crypto currency", "hardware-wallet", "security"]
---

Em 2013 tive meu primeiro contato com as chamadas crypto-moedas, achei muito interessante o conceito e resolvi fazer um teste. Comprei R$100,00 de uma alt-coin chamada Litecoin, deixei essa carteira jogada em algum canto. Em 2017 numa aula de segurança da informação, implementamos uma blockchain para entender o conceito e eu lembrei que tinha manuseado isso alguns anos antes, revirando meus arquivos encontrei a carteira e para minha surpresa, estava valendo R$1.700,00 - vendi e fiquei satisfeito.

De uns tempos pra cá tenho me interessado novamente sobre o assunto, mas não só por suas possibilidades financeiras. Estou interessado em tornar meus dados sensíveis mais seguro, pensando nisso abandonei o uso do g-drive e do dropbox como meu container de informações, também abandonei o gmail como meu e-mail para assuntos sensíveis(como dinheiro, imposto de renda ou qualquer outro tipo de informação que o big brother possa ter interesse).

Neste novo contato, diferente do primeiro estou preocupado em guardar informações de forma segura, é ai que entram as hardware-wallets.

## Possibilidades

Existem diversas opções comerciais, de diversos tamanhos e para todos os bolsos. Algumas são mais famosas como a [Ledger](https://ledger.com) que parte R$230,00 - mas como disse antes o céu é o limite, os valores podem chegar a casa dos milhares de Reais. Essa não é a minha realidade, então busquei uma alternativa.

Estas hardware-wallets funcionam mais ou menos desta forma:

![hardware](/images/hw-1.png)

Esse chip de criptografia é relativamente barato, algo em torno de U$2,00 e memória flash(a mesma utilizada em pen driver) - também não é tão cara, claro que para esse tipo de utilização precisamos usar uma memória categoria classe 10, [porque](https://en.wikipedia.org/wiki/SD_card#Class).

Montar esse hardware também não é coisa de outro mundo, mas uma placa cheia de wireup não pode ser considerado algo muito confiável.

![sample](/images/sample.jpeg)

## Criptografar por software

Uma abordagem mais simplifica, gera da mesma forma uma solução boa o suficiente para uso no cotidiano, de forma esquemática, algo mais ou menos assim:

![hardware 2](/images/hw-2.png)

Para fazer isso por software, o mundo do software livre nos ofertas algumas possibilidades:

* [TrueCrypt](https://en.wikipedia.org/wiki/TrueCrypt) descontinuado.
* [Veracrypt](https://www.veracrypt.fr/en/Home.html) em atividade e uma boa opção.
* [ZuluCrypt](http://mhogomchungu.github.io/zuluCrypt/) em atividade, uma boa opção e está no repositório do Debian/Devuan.

Optei pelo último por motivos óbvios.

## Configuração

Achei simples de configurar, escolhi meu melhor pen drive(kingston cat 10 de 4GB) - formatei como ext4 e segui o tutorial do zuluCrypt para criar meu *Encrypted container in a hardware*.

O que achei muito legal, é que agora toda vez que plugo minha harware-wallet no meu pc - abre uma caixa de dialogo pedindo a senha cadastrada na criação, totalmente integrado com o meu SO Linux. Feita a autenticação, eu posso usa-lo como um drive normal, colocando e apagando arquivos. O que era para ser uma solução exclusiva para uso com crypto moedas, foi expandido para muitas possibilidades bacanas.

Viva o software livre!

