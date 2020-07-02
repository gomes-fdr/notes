---
title: "Minhas notas sobre uso do git"
date: 2020-05-11
slug: "minhas-notas-sobre-uso-do-git"
tags: ["wiki", "git"]
draft: false
---


Para *trazer* os submodulos de um projeto:

	git submodule init

Para *atualizar* os submodulos:

	git submodule update

Para *chavear* para um branch especifico dos submodulos:

	git submodule foreach 'git checkout develop'

Para *traze*' as atualizações de todos os sbmodulos:

	git submodule foreach 'git pull'

Para *guardar* as alterações em uma pilha *anonima*:

	git stash

Para aplicar as alterações dessa pilha no branch corrente:

	git stash apply

Para guardar inclusive untracked files:

	git stash -u

Para listar a pilha de *stashes*

	git stash list

Para criar um novo branch a partir de um stash:

	git stash branch novo-branch

Para acessar um stash especifico, acessa através de stash@{n} - por exemplo:


	git stash apply stash@{2} # aplica o stash 2 ao branch corrent
	git stash drop stash@{2} # Apaga o stash 2 da pilha

Apagar a pilha de stash:

	git stash clear

## Comparar modificações

Configurar ferramenta de diff:


	git config --global diff.tool meld

Para comparar dois branches usando a ferramenta gráfica *Meld*:
	
	git difftool -d ticket-4581..develop
	
A lógica é a mesma para fazer um diff entre commits, basta substituir o nome do branch pelo hash do commit(os primeiros 6 digitos são o suficiente).

## Juntar commits

Para *juntar* varios commits em um só:


	git rebase -i HEAD~<n> # Onde n é a quantidade de commits que desejamos juntar.


Neste comando iterativo podemos juntar, squash ou remover algum commit que não queremos - para isso basta remover a linha pick que contém o commit(leia as instruções do modo iterativo).
