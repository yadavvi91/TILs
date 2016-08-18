## Copying and Pasting to and from Clipboard in bash with xclip

Often we want to interact with the clipboard to copy and paste data to it and from it respectively to bash. We can use `xclip` for this.

### Copying from bash to Clipboard

Sometimes we wish to copy output of a command to clipboard so that we can paste it somewhere else using `Ctrl-V`.


Say we want the output of the following command in our clipboard -

```bash
find . -type f -iname strings.xml | grep -v './res/values/strings.xml' | wc -l
```

If we want the value of the commands run above in our clipboard, we can use `xclip` like so -

```bash
vishal@vishal-T540p:~/Settings$ find . -type f -iname strings.xml | grep -v './res/values/strings.xml' | wc -l | xclip -selection c
245
vishal@vishal-T540p:~/Settings$ 
```

Now, this output of `245` has been copied to the clipboard and we can use `Ctrl-V` to get this value.


### Pasting from Clipboard to bash

Similarly, if we want to copy something from clipboard to our bash we can use `xclip` as well.

Suppose we want to search for a file `BatterySettingsService.java` that has been copied in our clipboard with `Ctrl-C`, we do it like this

```bash
vishal@vishal-T540p:~/Settings$ find . -iname $(xclip -selection clipboard -o)
./src/com/aries/batterysettingsservice/BatterySettingsService.java
vishal@vishal-T540p:~/Settings$ 
```

### Creating an alias for copy/paste from xclip

Using the commands - `xclip -selection c` and `xclip -selection clipboard -o` for copying and pasting to clipboard respectively becomes tedious. So, we can set **aliases** for them.

The following aliases can be added in `~/.bashrc` file -
```bash
alias setclip='xclip -selection c'
alias getclip='xclip -selection clipboard -o'
```

Now the commands mentioned above become much easier - 
```bash
# For Copying to Clipboard
vishal@vishal-T540p:~/Settings$ find . -type f -iname strings.xml | grep -v './res/values/strings.xml' | wc -l | setclip
245

# For Pasting from Clipboard
vishal@vishal-T540p:~/Settings$ find . -iname $(getclip)
./src/com/aries/batterysettingsservice/BatterySettingsService.java

```
