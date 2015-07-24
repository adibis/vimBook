#vimdiff

You can either vimdiff by vimdiff file1 file2. If you have both files open in splits, run :diffthis in both splits and vim will enter the diff mode.

###Keybindings

```vim
dp          " Put current difference in the other file. (Diff Put)
do          " Get the current difference from the other file. (Diff Obtain)
]c          " Go to the next diff.
[c          " Go to the previous diff.
<C-w>w      " Move between the diff splits.
:diffupdate " Recalculate the diff.
```

###Options

You can decide what vim considers a diff and what not. Following options can help reduce clutter in the diff output.

```vim
set diffopt+=iwhite " Ignore whitespaces in diff.
set diffopt+=icase  " Ignore case in diff.
```