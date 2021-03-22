---
title: "My Vim Setup"
slug: "my-vim-setup"
date: 2021-03-22T15:56:42-03:00
draft: false
tags: ["neovim", "tools"]
---

So, I decided to try VIM again! Yes this is another time to try VIM, and why do I try again? Because I want, because it is fun and it is very cool.

Said that, I will show the steps to get a very simple VIM editor, based on my experience.

## First things first

Use [NeoVim](https://neovim.io/) - Listen to me, all things become more easy with NeoVim and you don't need to worry about unnecessary setup(after all everybody use utf-8 in these days)

## Using plugins

Some time ago I listen that VIM it was not a text editor, but a meta-text editor. This meaning that we have a tool to configure as we want and this is very powerful and could be very confuse too.

Here we meet the plugins and VIM offer a lot of possibilities, I strong recommend to use [VimPlug](https://github.com/junegunn/vim-plug). Because it is very simple and blaze fast!

Be careful and avoid to get or setup things that you never use, It could become a great mess! Take a look in my `~/.config/nvim/init.vim`:

	1  call plug#begin()
	2  Plug 'morhetz/gruvbox'
	3  Plug 'junegunn/goyo.vim'
	4  Plug 'matze/vim-move'
	5  call plug#end()

	6  syntax enable
	7  set encoding=UTF-8
	8  set number
	9  set relativenumber
	10 set background=dark
	11 set mouse=a
	12 set spell spelllang=pt_br,en_us

	14 colorscheme gruvbox

	15 nnoremap <C-G> :Goyo <cr>

Between lines 1..5 we have the plugins that we are using:

* gruvbox: It is a theme, to make the visual more attractive.
* goyo: It is a distraction free, to keep the focus when you are writing.
* vim-move: To make easy move lines to up and down.

Line 6 we enable syntax highlight.

Line 7 Set the encode ;op

Line 8 turn on line numbers.

Line 9 very cool features, just give a try.

Line 10 dark themes saving eyes.

Line 11 sometimes we need a mouse.

Line 12 if you wanna write some docs, this is very important.

Line 14 turn on the theme that we install on the plugins.

Line 15 make a key map to turn on/off the goyo mode.

## That is it!

Of course if you need more features, probably you will need more plugins - Be careful, keep things simple it is a bless!

