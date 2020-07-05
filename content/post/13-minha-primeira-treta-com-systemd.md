---
title: "Minha Primeira Treta Com Systemd"
date: 2020-07-05
slug: "minha-primeira-treta-com-systemd"
tags: ["linux"]
draft: false
---

Recentemente parei de usar a distribuição Linux [Debian](https://debia.org) e seus derivados, nada a ver com a qualidade em si. Mas eu não quero mais ter que instalar um sistema a cada nova *release*, fica fácil deduzir que fiz a troca por uma distro *rolling release*, [Manjaro](https://manjaro.org) para ser mais especifico.

Estou muito satisfeito, como um bom exemplo de como tem facilitado minha vida, posso citar a necessidade de usar libs de Qt4 em alguns projetos e isso ser facilmente suportado pelo gerenciador de pacotes da distro, o [Pacman](https://www.archlinux.org/pacman/). Para fazer isso na versão mais atual do Ubuntu, 20.04 é um parto de aranha(gíria local para muito difícil).

Mas como nem tudo são flores, resolvi usar um servidor de [DLNA](https://en.wikipedia.org/wiki/Digital_Living_Network_Alliance) para servir arquivos de vídeo para minha TV smart. Tudo muito bem, tudo muito bom, mas ai veio a ginastica necessária para fazer o [Minidlna](https://sourceforge.net/projects/minidlna/) funcionar - instalar foi mega fácil, mas a partir disso, só tristeza.

Editar o arquivo de configurações, perfeito.

Criar regras de acesso ao diretório home.

Criar regras ACL.

Criar regras, criar regras, etc...

Baixei uma [imagem docker](https://github.com/geekduck/docker-minidlna) baseada no [Alpine Linux](https://www.alpinelinux.org), que não usa [Systemd](https://en.wikipedia.org/wiki/Systemd). Voalá, só funciona!

Isso me fez questionar o uso do [Systemd](https://nosystemd.org/), logo agora que minha máquina tinha ficado redondinha, vou viver com isso mais um tempo, espero que não vire um calo no meu sapato.

Não curto esse lance de [Distro Hopping](https://www.linux-magazine.com/Online/Blogs/Off-the-Beat-Bruce-Byfield-s-Blog/Distro-hopping), fiquei anos no Slackware e décadas no Debian, vou continuar no Manjaro, por enquanto. Seria muito legal se as distros oferecessem a opção de usar ou não systemd.