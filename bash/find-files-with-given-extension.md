Finding all the files in a directory with an extension of a given type.
===

```bash
find . -maxdepth 1 -type f -name '*.txt'
```

This command *finds* all the files in the current directory *(and not sub-directories)*
which are of type file *(not directory)* and which have an extension `.txt`.

Here, `.` refers to the current directory, `-maxdepth 1` means that we do not have
to go to sub-directories to find the files, `-type f` tells that we are only searching
for files (not directories) and `'*.txt'` is a glob which matches any file that with
extension *.txt*
