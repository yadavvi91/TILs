Copy and Paste to the System Clipboard
===

We sometimes need to copy and paste text to the System Clipboard from and to ***vim***.
The `"` register of ***vim*** can be used for this.

####Copying from vim to the System Clipboard

When using an `X11 System` like Linux, to copy text to the ***System Clipboard***,
do the following thing -

 * Enter in the Normal mode (i.e. if in any mode like `insert` etc. press `Esc`).
 * Move the cursor to the point where you want to copy.
 * Enter the following command - 

   ```vim
   "+2yy
   ```
   to copy 2 lines from the cursor to the system clipboard.
   
If we want to ***visually select text*** and then copy to the clipboard we can do this -

 * Enter in the Normal mode (i.e. if in any mode like `insert` etc. press `Esc`).
 * Move the cursor to the point where you want to copy.
 * Visually select text using `v` or `Ctrl-v` or `Shift-v` (**do not** `yank` i.e. press `y`).
 * Enter the following command now -

   ```vim
   "+yy
   ```

Now, the lines that were selected are copied to the clipboard.


####Pasting from System Clipboard to VIM

To paste text *from* ***System Clipboard*** *to* ***VIM*** follow these steps - 

 * Enter in the Normal mode (i.e. if in any mode like `insert` etc. press `Esc`).
 * Move the cursor to the point where you want to paste.
 * Enter the following command - 
 
   ```vim
   "+p
   ```
