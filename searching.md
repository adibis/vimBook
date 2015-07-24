#Searching

###Keybindings

```vim
/   " Search forward
?   " Search backward
n   " Go to next match
N   " Go to previous match
*   " Forward search word under cursor
#   " Backward search word under cursor
```

###Options

```vim
set hlsearch    " Highlight search results.
set ignorecase  " Make searching case insensitive
set smartcase   " ... unless the query has capital letters.
set incsearch   " Incremental search.
set gdefault    " Use 'g' flag by default with :s/foo/bar/.
set magic       " Use 'magic' patterns (extended regular expressions).

" Use <C-L> to clear the highlighting of :set hlsearch.
if maparg('<C-L>', 'n') ==# ''
  nnoremap <silent> <C-L> :nohlsearch<CR><C-L>
endif
```

###Replace

```vim
:%s/search/replace/     " Search and replace
:%s/search/replace/cgi  " Global search and replace with confirmation
```