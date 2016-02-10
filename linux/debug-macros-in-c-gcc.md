Using DEBUG macros in C programs with gcc
===

Languages have complex control structures like exceptions to pass error
conditions around. 

C tackles the problem by returning error codes and
setting a global `errno` value that you check. C uses `debug macros` to
implement basic debugging and error handling.

When a C program is compiled, the first step that the compiler takes is
to run the preprocessor, which processes all the preprocessor directives,
those lines that begin with the pound sign `#`. There are options that
control how the preprocessor behaves, and these are important to know and
understand. The most important are - 

1. how to define symbols on the command line, and
2. how to tell the preprocessor where to look for include-files.

```
-D name                           This produces 'name' as a macro symbol, with
                                  value 1,or 'true' (because anything not 0 in C
                                  is 'true')

-D name=definition                The contents of definition are tokenized and
                                  processed as if they appeared during
                                  translation phase three in a '#define' directive.
                                  e.g.
                                          gcc -D testvalue=6 -o myprog myprog.c
                                  is the same as if you had placed
                                          #define testvalue 6
                                  in myprog.c
```

Similarly, we can unset the `#define` variables using either `-U name` **OR** `-undef`

Using `gcc -D`

```bash
Syntax:
    gcc -D name [options] [source files] [-o output files]
    gcc -D name=definition [options] [source files] [-o output files]

myprog.c

    #include <stdio.h>

    int main()
    {
        #ifdef DEBUG
            printf("Debug run\n");
        #else
            printf("Release run\n");
        #endif
    }

Using -D option if we compile and run
    $ gcc -D DEBUG myprog.c -o myprog
    $ ./myprog
    Debug run
    $

And if we DO NOT use the -D option
    $ gcc myprog.c -o myprog
    $ ./myprog
    Release run
    $

```

#### Further Reading:
http://www.compsci.hunter.cuny.edu/~sweiss/resources/The%20GCC%20Compilers.pdf
http://resources.mpi-inf.mpg.de/departments/rg1/teaching/advancedc-ws08/script/lecture07.pdf
http://stackoverflow.com/questions/1644868/c-define-macro-for-debug-printing
http://blog.justinlintz.com/2011/09/useful-c-debug-macro/
http://c.learncodethehardway.org/book/ex20.html
