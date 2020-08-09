---
title: "Ainda Sobre Ambiente De Trabalho"
date: 2020-08-08T21:52:20-03:00
slug: "ainda-sobre-ambiente-de-desenvolvimento"
tags: ["linux"]
draft: false
---

Tenho procurado o melhor, ser mais produtivo e organizado. A maneira como organizamos nossas ideias refletem de forma direta no cotidiano e na qualidade do que produzimos.

Gosto das coisas simples, acredito que por isso a maneira Unix de pensar projetos e ferramentas sempre me cativou, fiz algumas experiências nos últimos meses. Saí da base Debian, na qual estava a mais de uma década, testei o Slackware, Manjaro, Artix e Debian novamente.

No PC de trabalho uso xUbuntu 18.04 estou bem ambientado com esse desktop, não tinha conseguido a mesma produtividade combinada com a beleza desta distro. Finalmente acredito ter chego a um bom equilíbrio, a figura abaixo tenta resumir isso.

![Escolhas](/images/escolhas.png)

Tem que ser Linux, é o maior projeto opensource do mundo e talvez o mais bem sucedido.

Precisa ser estável, quando digo isso lembro da minha breve experiência com Artix, Manjaro se mostrou um projeto bem maduro e estável mas, entra o terceito ponto.

Sem systemd, recentemente o Luke Smith postou um [vídeo](https://youtu.be/wgg3pt9in00) falando sobre isso. Estamos chegando num ponto que não é a distro que contém o systemd e sim o contrário. Vai totalmente na contra mão da filosofia do Unix, fazer bem apenas uma coisa. Grandes complexidades devem ser resolvida, combinando a capacidade de ferramentas simples, conectando-as.

O projeto [Devuan](https://devuan.org) promete entregar isso.

  1. Simples
  2. Estável
  3. Sem systemd

## Ajustes

Precisei fazer alguns ajustes depois da instalação no meu notebook pessoal.

  1. [Fix do pulse audio](https://dev1galaxy.org/viewtopic.php?id=3620)
  2. [Fix do touchpad](https://dev1galaxy.org/viewtopic.php?id=3317)
  3. Instalação do tema do xUbuntu:
  	
	sudo apt install greybird-gtk-theme
	sudo apt install elementary-xfce-icon-theme

Por terem portado o Debian Buster, tenho mais de 50K pacotes a disposição.

![Meu PC](/images/meu-pc.png)
