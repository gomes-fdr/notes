---
title: "Setup de um Linux para DESENVOLVEDOR"
date: 2020-05-14
slug: "setup-de-um-linux-para-dev"
tags: ["wiki", "linux"]
draft: false
---

O ambiente de trabalho, no caso uma máquina com Linux, reflete diretamente na qualidade da execução de tarefas, para desenvolvedores de softwares é fortemente recomendado um ambiente simples, robusto e estável. Pensando nisso, neste vasto universo de distribuições, duas opções bem ortodoxas se destacam. Debian e Slackware, você estará muito bem servido com qualquer uma delas, neste tutorial vamos explorar o Slackware Linux, por que?! Porque é divertido!

## Instalação
Vou considerar que temos uma instalação de Slackware Linux nova, aqui temos duas possibilidades no que toca instalações:

  * Sem UEFI: Para máquinas com BIOS de antes de 2008(eu acho), no momento de fazer as partições do HD(usando cfdisk) escolher a opção *dos*;
  * Com UEFI: Máquinas com BIOS pós 2008, no momento de fazer as partições do HD(usando cfdisk) escolher a opção *gpt*;

## Esquema de partições
Aqui vamos primar por um esquema simples também:

  * Sem UEFI: 
    * sda1: para /, ext4, 50GB
    * sda2: para /home, ext4, o que sobrou de espaço em disco após criar sda3
    * sda3: para swap - a regra para o tamanho do swap é 2XRAM, sendo no máximo 8GB de tamanho(na prática 4GB de swap resolve tua vida).
  * Com UEFI: Um pouco mais complexo, este [vídeo](https://youtu.be/fd0FvvsGaUM) é uma excelente referência.

Embora a instalação seja importante, considero que a pós-instalação é o que realmente faz a diferença, vamos lá!

## Pós-instalação
A partir deste ponto é onde quero levantar os diferenciais, na minha modesta opinião.

Ao final de uma instalação de Slackware, temos apenas um super usuário e nada mais, vamos começar a preparar nosso ambiente para não precisarmos nos preocupar com eventuais quebras por instalações/atualizações desnecessárias.

  1. Conectar na internet: Temos duas opções, a mais tradicional, usando um cabo de rede. Ou caso estejamos usando um notebook, devemos instalar o pacote que está no dvd de instalação do Slackware, na seção extra/wicd chamado wicd-xxx.txz, com ele instalado podemos utilizar o comando `wicd-curses` no terminal e fazer nossa conexão com a rede que desejamos. Aqui é importante lembrar que o serviço NetworkManager deve estar ativo(`chmod +x /etc/rc.d/rc.networkmanager`)
  2. Após logar como root, vamos escolher um mirror no arquivo /etc/slackpkg/mirrors: Escolha um mirror do Brasil, não vou utilizar o slackware current(não é o objetivo aqui) execute:

		slackpkg upgrade
		slackpkg upgrade-all

Após esse procedimento seu slackware estará atualizadissimo!

## Instalando novos software
O Slackware tem a má fama de não possuir nenhum gerenciador de pacotes, o que já verificamos não ser verdade no item *pós-instalação*. Agora vamos adicionar novas ferramentas a nossa caixa de desenvolvimento, o [sbopkg](https://sbopkg.org/) é um facilitador para acessarmos o repositório de receitas do [slackbuilds](https://slackbuilds.org/). 

  1. Baixar o pacote sbopkg-xxx.tgz e instala-lo com o `installpkg sbopkg-xxx.tgz`;
  2. A partir daqui sempre vamos executar o `sbopkg` para fazer a instalação de novos pacotes no nosso Slackware.

## Próximos passos
No próximo tutorial vamos configurar um WM(Windown Manager) e adicionar mais ferramentas na nossa caixa de desenvolvimento.
