---
title: "Oh my bash!"
date: 2020-06-01
slug: "oh-my-bash"
tags: ["bash"]
draft: false
---

[Oh my bash](https://ohmybash.github.io/) é um daqueles projetos que não podem faltar na caixa de ferramentas de qualquer um que use um terminal como base para executar ou mesmo editar código em sistemas baseados em Linux.

Mas do que se trata isso?
Para que serve?

Bom quando abrimos um terminal, normalmente temos algo do tipo:

	usuario@host: 
	
Não deixa de ser uma informação útil, mas podemos tornar isso muito mais interessante. É ai que entra os serviços do oh-my-bash, vamos lá.

	sh -c "$(curl -fsSL https://raw.github.com/ohmybash/oh-my-bash/master/tools/install.sh)"
	
Isso nos dá um prompt do tipo:

	08:22:04 usuario@host ~ →
	
Mas não mudou nada! Calma lá cara pálida, essa ferramenta adiciona algumas funcionalidades interessantes ao nosso prompt, por exemplo:

  * Informações sobre um repositório git
  * Informações sobre o uso de ambientes virtuais(como o `virtualenv` do python)

Um exemplo de prompt:

	|venv-3.8.2| host in ~/tmp
	○ → 
	
Outro exemplo estando dentro de um projeto versionado pelo git:
	
	host in ~/.oh-my-bash
	± |master ✓| → 
	
Este prompt está usando o tema `tylenol`, os temas estão em: `$HOME/.oh-my-bash/themes` e são escolhidos no arquivo de configuração `.bashrc` - vale a pena explorar.

