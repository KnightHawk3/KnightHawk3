---
layout: post
title: "My vimfiles"
date: 2013-05-02 07:23
comments: true
categories: Vim, Linux, Unix
---

I put a good amount of work into my Vim configuration, here is some documentation for it.

```
"""""
" KnightHawk3's vimrc Knight Hawk3 (KnightHawk3.com)

"""
" Pathogen *cough cough*
call pathogen#runtime_append_all_bundles()
call pathogen#helptags()
```

So this will open all the plugins in $VIMHOME/bundle/ and use them, this saves your vimfiles from being a convoluted mess, it then appends the help files, since I always forget to run helptags manually.


```
"""
" Nerdtree
map <C-n> :NERDTreeToggle<CR>
autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTreeType") && b:NERDTreeType == "primary") | q | endif " Close if its the last one
```

The first is a mapping that allows me to press ```ctrl-n``` to open a NERDTree menu, it also closes it if it is open, the next line closes Vim if NERDTree is the last window open.

```
"""
" Filetypes
filetype on
filetype plugin indent on
```

This enables automatic filetype detection, pretty standard

```
"""
" Autocompletion
au FileType python set omnifunc=pythoncomplete#Complete
let g:SuperTabDefaultCompletionType = "context"
set completeopt=menuone,longest,preview
```

These are some autocompletion options, allowing me to use tab complete in python and pretty much everything.

```
"""
" Settings
set nocompatible " Oh my god yes.
set scrolloff=5  " Basically, doesn't let your cursor get to the top of the screen
set number	 " Line numbers
```

Sets nocompatible, you should have that already. Then my scrolloff, so that if my cursor is 5 lines from the top or bottom the window will start scrolling, this stops me from going to the bottom line. Finally it turns on line numbers

```
" Seaching settings
set ignorecase	 " Ignores case in searching
set showmatch	 " Highlight matches
" Indentation settings
set tabstop=4    " 4 ts master race
set shiftwidth=4 " For the love of god.
set backspace=2  " Real backspacing
set expandtab    " Tabs become spaces
" Prettyness
set showcmd	     " Just so I can see
set laststatus=2 " For Powerline
```

Some settings that set various things, should be rather self explanatory.

```
"""
" Mappings
"
let mapleader = ","

" \mdhtml converts document to html5
nmap <leader>mdhtml :%!pandoc -f markdown -t html5<cr>
" \mddtex converts to latex
nmap <leader>mdtex :%!pandoc -f markdown -t latex --template=default.latex<cr>

" \v opens my vimrc for editing
map <leader>v :tabe ~/vimfiles/.vimrc<cr>

map <leader>fb :FufBuffer
map <leader>ff :FufFile
```

This sets my mapleader to ```,``` so that I can have various bindings.

I then go on to set some cool bindings such as:

* ```,mdhtml``` this converts the current document from markdown to html5, using pandoc, pandoc must be installed.
* ```,mdtex``` this converts the current document from markdown to tex, using pandoc again.
* ```,v```  this opens my ```~/vimfiles/.vimrc``` for editing, TODO: change this to be dynamic.
* There are then some bindings for Fuzzy finder


```
" Tagbar on ,tb
nmap <leader>tb :TagbarToggle<CR>
```

This toggles tagbar on ```,tb```

```
" Tasklist on \td
map <leader>td <Plug>TaskList
" Hitting & on a word allows me to substitute that word in the current
" paragraph with the smallest number of keypresses I could come up with.
" Basically it puts the first part of a s/word/letter on the commmand line
" waiting for me to type the replacement and hit <CR>
nnoremap & :'{,'}s/<c-r>=expand('<cword>')<cr>/
```

* 

```
" jk leaves insert mode
inoremap jk <ESC>
```

```
" Tasklist
map <leader>td <Plug>TaskList
```

```
" Window movement
map <c-j> <c-w>j
map <c-k> <c-w>k
map <c-l> <c-w>l
map <c-h> <c-w>h
```

```
"""
" GUI stuff

"My font for the GUI, removing of some buttons, and UTF-8
set encoding=utf-8
set guifont=Consolas\ for\ Powerline\ FixedD:h12
set guioptions=egmrt
```

```
" Theme
set background=light
let g:solarized_termtrans=1
let g:solarized_termcolors=256
let g:solarized_contrast="high"
let g:solarized_visibility="high"
syntax on
colorscheme solarized
```
