# Navigating Files

###Keybindings

```vim
gg          " Go to the top of the file.
G           " Go to the bottom of the file.
gf          " Open file under cursor
<C-w>f      " Open file under cursor in a horizontal split.
<C-w>gf     " Open file nuder cursor ina new tab.
```

###Options

Sometimes there are special symbols and characters around the filename which can confuse vim. It will give an error that file is not accessible or not found. Following options will limit what vim considers part of a valid filesystem path.

```vim
set isfname-=:  " Remove :
set isfname-==  " Remove =
set isfname-=+  " Remove +
```