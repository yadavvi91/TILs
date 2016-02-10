Using `<unistd.h>` in C programs
===

In C and C++ programming languages, `<unistd.h>` is the name of the
header file that provides access the the POSIX operating system API (Linux
API).

On Unix-like systems, the interface defined by `<unistd.h>` is typically
made up largely of ***system call wrapper functions*** such as `fork`, `pipe`
and I/O primitives (like `read`, `write`, `close`, etc.).

Wherever you use `<unistd.h>` it is also important to include
`<sys/types.h>`, because `<sys/types.h>` header file contains type definitions
like `pid_t`, `size_t`, `ssize_t`, `uid_t` etc. A `fork()` call returns a 
**ProcessId** of type `pid_t`.

#### The `fork()` system call

The `fork()` system call will *spawn a new child process which is an
identical process to the parent except that has a new* ***system process ID***.

The process is copied in memory from the parent and a new process
structure is assigned by the kernel. The return value of the function is
what distinguishes the two threads of execution.

On success, a **0** is returned by the fork function in the child's process.

The *environment, resource limits, umask, controlling terminal, current
working directory, root directory, signal masks and other process resource*
are also duplicated from the parent in the forked child process.


```C
#include <stdio.h>
#include <string.h>

// Required for fork()
#include <sys/types.h>
#include <unistd.h>

#include <stdlib.h>

int global_var = 2;

int main()
{
    char s_identifier[512];
    int i_stack_var = 20;

    pid_t p_id = fork();
    if (p_id == 0) {            // child
        // Code only executed by child process
        strcpy(s_identifier, "Child Process: ");
        global_var++;
        i_stack_var++;
    } else if (p_id < 0) {        // failed to work
        fprintf(stderr, "Failed to fork");
        exit(1);
    } else {        // Parent
        // Code only executed by parent process
        strcpy(s_identifier, "Parent Process: ");
    }

    printf("%s", s_identifier);
    printf(" Global variable: %d", global_var);
    printf(" Stack variable:  %d\n", i_stack_var);

    return(0);
}

Compile:    gcc -o forktest forktest.c
Run:        ./forktest

Output:

Parent Process: Global variable: 2 Stack variable: 20
Child Process:  Global variable: 3 Stack variable: 21

```


#### Further Reading:

Links -
* http://www.yolinux.com/TUTORIALS/ForkExecProcesses.html
* http://www.cs.cf.ac.uk/Dave/C/node22.html
* http://en.wikipedia.org/wiki/Unistd.h

and Books -

* Advanced Linux Programming - Mark Mitchell, Jeffrey Oldham et. al.
* Advanced UNIX Programming - Marc J. Rochkind
* Advanced Programming in the UNIX environment - W. Richard Stevens

