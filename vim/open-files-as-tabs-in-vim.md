Opening files as tabs in vim.
===

To open multiple files in `vim` in different tabs use the `-p` option.
```vimrc
vim -p file1 file2 file....
```

There are many commands that directly create or close tabs:

```vimrc
:tabedit {file} edit specified file in a new tab
:tabfind {file} open a new tab with filename given, searching the 
                'path' to find it
:tabclose       close current tab
:tabclose {i}   close i-th tab
:tabonly        close all other tabs (show only the current tab)
```

Navigating between tabs in vim.
```vimrc
:tabs        list all tabs including their displaying windows
:tabm 0      move current tab to first
:tabm        move current tab to last
:tabm {i}    move current tab to position i+1

:tabn        go to next tab
:tabp        go to previous tab
:tabfirst    go to first tab
:tablast     go to last tab
```

In Normal mode we can also use the following for navigation.
```vimrc    
gt           go to next tab
gT           go to previous tab
{i}gt        go to tab in position i
```
To get the help for tabs we can use.

```vimrc
:tab help
```

