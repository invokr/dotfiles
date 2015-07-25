let g:python_host_prog='/usr/bin/python2.7'

" Plugins
call plug#begin('~/.nvim/plugged')
Plug 'sickill/vim-monokai'
Plug 'bling/vim-airline'
Plug 'Valloric/YouCompleteMe', { 'do': './install.sh' }
Plug 'scrooloose/nerdtree'
Plug 'Xuyuanp/nerdtree-git-plugin'
Plug 'jistr/vim-nerdtree-tabs'
Plug 'tpope/vim-fugitive'
Plug 'scrooloose/syntastic'
call plug#end()

" General
set autoread
set encoding=utf8

let mapleader = ","
let g:mapleader = ","

" Intendation
set expandtab
set tabstop=4
set shiftwidth=4
set ai
set wrap

" UI
syntax enable
colorscheme monokai

set nu
set ruler
set noerrorbells
set novisualbell

set laststatus=2
let g:airline_theme="papercolor"

map <Leader>nn :NERDTreeTabsToggle<CR>
tnoremap <Esc> <C-\><C-n>

" Search and replace
set ignorecase
set smartcase
set hlsearch
set incsearch
set showmatch
set magic

" Do not create those pesky temp files
set nobackup
set nowb
set noswapfile

" Clang Format
let g:clang_format_bin = "/usr/bin/clang-format-3.5"

function ClangFormat()
    write
    silent execute "!" . g:clang_format_bin . " -i " . bufname("%")    
    e
endfunction

command -bar -nargs=0 ClangFormat call ClangFormat()
nmap <Leader>f :ClangFormat<CR>

" Show and Trim spaces
function ShowSpaces(...)
  let @/='\v(\s+$)|( +\ze\t)'
  let oldhlsearch=&hlsearch
  if !a:0
    let &hlsearch=!&hlsearch
  else
    let &hlsearch=a:1
  end
  return oldhlsearch
endfunction

function TrimSpaces() range
  let oldhlsearch=ShowSpaces(1)
  execute a:firstline.",".a:lastline."substitute ///gec"
  let &hlsearch=oldhlsearch
endfunction

command -bar -nargs=? ShowSpaces call ShowSpaces(<args>)
command -bar -nargs=0 -range=% TrimSpaces <line1>,<line2>call TrimSpaces()

nmap <Leader><Space>   :TrimSpaces<CR>
