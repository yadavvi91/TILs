Search and remove leading and trailing whitespace in a file
====

A file often contains leading and trailing whitespace character *(a space or a tab)*.
We can use VIM commands to remove unwanted space whitespaces.

In a search, `\s` finds whitespace *(a space or a tab)* and `\+` finds one
or more occurrences.

*for e.g.* -

to delete all the trailing whitespace (at the end of each line) -

```vim
:%s/\s\+$//
```

Here, the `$` is an anchor for the end of line. So, all the whitespace
characters at the end of the line are matched by `\s\+$`.

Since we are replacing the whitespace characters with nothing,
we can even omit the substitution as follows -

```vim
:%s/\s\+$
```

Similarly, to delete the leading whitespace at the beginning of each line -

```vim
:%s/^\s\+
```
