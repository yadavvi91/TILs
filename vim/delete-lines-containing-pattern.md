Delete all lines containing a pattern in VIM
===

The ***ex*** command `g` is very useful for acting on lines that match a
pattern. We can use it with the `d` command, to delete all the lines that
contain a particular pattern, or all the lines that do not contain a pattern.

To delete all lines containing a pattern - say *profile* we do this -
```bash
:g/profile/d
```
---

Deleting all lines containing that are empty or contain only whitespace
```bash
:g/^\s*$/d
```
>**NOTE:** `\s` stands for whitespace character, `^` and `&` are anchors which mean
*beginning* and *end of line* respectively.

---

To delete all the lines that do **NOT** contain a pattern, use `g!` instead
of `g`
```bash
:g!/^\s*"/d  #(Lines that are not starting with a ")
```
	
We can also use `v` instead of `g!` to match lines **NOT** containing a
pattern.
