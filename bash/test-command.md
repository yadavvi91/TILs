Various types of `test` command
===

To test expressions in Shell/bash we do this -
```bash
test expression
```
OR the more popular version -
```bash
[ expression ]
```
OR more recent version -
```bash
[[ expression ]]
```

*for e.g.:*

```bash
FILE=~/.bashrc
if [ -f "$FILE" ]; then
        echo "$FILE is a regular file."
fi

if [[ $(id -u) -eq 0 ]]; then
        echo "super user."
fi
```
------------------------------------------------------------------------

#### `(( ))` - Designed For Integers

Just as `[[ ]]` is used for normal test - `(( ))` is used for Integers

*for e.g.:*
```bash
if ((1)); then echo "It is true."; fi
```
