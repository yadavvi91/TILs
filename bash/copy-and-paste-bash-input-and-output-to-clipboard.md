## Copying and Pasting to and from Clipboard in bash with xclip

Often we want to interact with the clipboard to copy and paste data to it and from it respectively to bash. We can use `xclip` for this.

### What is `xclip`?

The **X Window System** (**X11**, or shortened to simply **X**) is a windowing system for bitmap displays, common on UNIX-like computer operating systems.

**X Window selection**: Selections, cut buffers, and drag-and-drop are the mechanisms used in the **X Window System** to allow a user to transfer data from one window to another. 

`xselection`, `xclip`, `xsel` and `xcopy` are command line programs that copy data to or from the **X selection**.

### Copying from bash to Clipboard

Sometimes we wish to copy output of a command to clipboard so that we can paste it somewhere else using `Ctrl-V`.


Say we want the output of the following command in our clipboard -

```bash
vishal@vishal-T540p:~/Settings$ find . -type f -iname strings.xml | grep -v './res/values/strings.xml' | wc -l
245
```

If we want the output of the commands run above in our clipboard, we can use `xclip` like so -

```bash
vishal@vishal-T540p:~/Settings$ find . -type f -iname strings.xml | grep -v './res/values/strings.xml' | wc -l | xclip -selection clipboard
vishal@vishal-T540p:~/Settings$ 
```

Now, the output `245` has been copied to the clipboard and we can use `Ctrl-V` to get this value.

#### Removing the extra `\n` at the end of an output

The output of a command sometimes has an extra `\n` character which we might not want. We can remove the extra `\n` at the by adding an `xargs echo -n` and then `pipe(|)` the data to `xclip`. We can modify the command above by doing so - 

```bash
vishal@vishal-T540p:~/Settings$ find . -type f -iname strings.xml | grep -v './res/values/strings.xml' | wc -l | xargs echo -n | xclip -selection clipboard
vishal@vishal-T540p:~/Settings$ 
```

### Pasting from Clipboard to bash

Similarly, if we want to copy something from clipboard to our bash we can use `xclip` as well.

Suppose we want to search for a file `BatterySettingsService.java` that has been copied in our clipboard with `Ctrl-C`, we do it like this

```bash
vishal@vishal-T540p:~/Settings$ find . -iname $(xclip -selection clipboard -o)
./src/com/aries/batterysettingsservice/BatterySettingsService.java
vishal@vishal-T540p:~/Settings$ 
```

### Creating an alias for copy/paste from xclip

Using the commands - `xargs echo -n | xclip -selection clipboard` and `xclip -selection clipboard -o` for copying and pasting to clipboard respectively becomes tedious. So, we can set **aliases** for them.

The following aliases can be added in `~/.bashrc` file -
```bash
alias setclip='xargs echo -n | xclip -selection clipboard'
alias getclip='xclip -selection clipboard -o'
```

Now the commands mentioned above become much easier -

```bash
# For Copying to Clipboard
vishal@vishal-T540p:~/Settings$ find . -type f -iname strings.xml | grep -v './res/values/strings.xml' | wc -l | setclip
```

```bash
# For Pasting from Clipboard
vishal@vishal-T540p:~/Settings$ find . -iname $(getclip)
./src/com/aries/batterysettingsservice/BatterySettingsService.java
```
