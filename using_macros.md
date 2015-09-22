#Vim Macros

Macros are one of the best things in VIM for doing repetitive edits. Let's consider an example where you want to get rid of all the file names in the following list. 

```
/path/to/file.ext, required_text1, /other/random/things
/paths/to/other/file.ex, required_text2, /some/more/
/this/path/to/file.ext, required_text3, /and/even/more/file.xtx
/other/paths/to/other/file.ex, required_text4, /this/too/
/something/else/and/newfile.tx,  required_text5, /and/this/as/well
```

One way to do it is to go on each line and delete the unwanted data. Other option is to use Vim macros and do it for one line. Then just execute the macro for all others. Let's see how. 

You can record a macro with ```q<register>```. Let's record it in the ```q``` register itself for now. Then we will execute all the commands we want and finally stop recording the macro. Here's how the steps will look: 

```vim
qqq " Clear the q register.
qq  " Start recording  in q register.
... " Sequence commands here.
q   " Stop recording.
@q  " Execute the q macro.
```

So to do what we want in the example above, position the cursor at the start of the first line. Then execute ```qqqqq``` to clear and start recording in ```q``` register. Followed by, 

```vim
vf,  " Select (until you) find a comma.
l    " Move cursor right once.
d    " Delete the selected data.
f,   " Move to the next comma.
v$   " Select till end of line.
h    " Move selection to left (to avoid moving next line up)
d    " Delete the selected data.
0j   " Go to the start of next line.
```

Now press ```q``` again to save this macro. Now if you execute the command ```@q``` you will see that the same operations will be performed on the second line and cursor will move to the start of next line.

You can record multiple commands like this in different registers and use them wherever necessary. This is much faster than writing a script for doing such manipulation.

##Saving Macros

Once you start using macros regularly, you will notice that you keep reusing the same macros multiple times. In such a case, it's best to save the macro in your vimrc so it will always be available to you when you start vim.

You can use ```:registers``` command to list all saved macros. In our current example, use ```:reg q``` to view contents of ```q``` register. You will see something like ```"q vf,ldf,v$hd0j```. This can now be saved in your vimrc file as: ```let @q='vf,ldf,v$hd0j'```. Now every time you start vim, you can execute ```@q``` to run this macro.

##Editing Macros

There are times when you will screw up a macro. If it has 20 commands, redoing everything will consume more time than simply redoing the edit per line. You can do that by the following commands. Let's say we want to also change the case of the first letter in the ```required_text``` in the current macro. ```:let @q='<C-r><C-r>q``` will paste the contents of the ```q``` register on the vim command. You can edit them, append ```'``` at the end and hit enter to save the macro. In our case it will be, ```let @q='vf,ldf,v$hd0~0j'```.