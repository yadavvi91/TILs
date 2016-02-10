The substitute command of VIM.
===

`:substitute` or `:s` or `:su` is used to substitute *i.e.* search and replace
for files in an opened file in VIM.

To open help about `:substitute` in VIM use - 
```bash
:help :substitute
```

The format of using `:substitute` is -

```bash
:[range]s[ubstitute]/{pattern}/{string}/[flags] [count]
```

---
**range** can be specified like - `<4,>` OR `<%>` (means 1,$ i.e. from 1 to last line).

*for e.g.* 
* `21,25s/bash/BASHED/g` replaces all occurrences of *bash* with *BASHED* from lines
21 to 25 (both inclusive).
* `%s/bash/BASHED/g` replaces all occurrences of *bash* with *BASHED* from lines
in all lines in the file.

---
**flags** that can be used are -
* `g` - replace all occurrences in the line.  Without this argument,
replacement occurs only for the first occurrence in each line.
* `c` - ask for every substitute.
* `i` - case insensitive
* `I` - case sensitive

*for e.g.* 
* `21,25s/bash/BASHED/g` replaces all occurrences of *bash* with *BASHED* from lines
21 to 25 (both inclusive).
* `21,25s/bash/BASHED/gc`, here because of the `c` flag, the `substitute` command
asks whether we want to change *all, none, etc.* like so - 
`replace with BASHED (y/n/a/q/l/^E/^Y)?`

---
**count** can only be used when the initial **range** is NOT specified

*for e.g.*
* `s/bash/BASHED/g 5` replaces 5 instances of *bash* with *BASHED* from the cursor location.
We can see that no range is specified with `s` (substitute) command here.
(NOTE: `%s` means *all the lines*, **not** no lines).

---
##### Special uses:
Find the count of a match from some line to some other line - 
```bash
%s/{pattern}//n
```