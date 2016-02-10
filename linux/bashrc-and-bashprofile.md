`.bashrc` and `.bash_profile` in Linux
======


Sometimes we need to add some environmental variables for a shell
like `PATH`, `JAVA_HOME` etc. But we often face a problem, whether to put
those variables in `.bashrc` or `.bash_profile` files?

Sometimes only one of the files exist. Why the difference?

---

There are 2 types of shell -
 * ***login shell***
 * ***non-login shell***

`.bash_profile` is executed for ***login shells***, while `.bashrc` is executed
for ***non-login shells***.

Whenever we open a shell prompt one/both of these files (`.bashrc` and
`.bash_profile` are executed).


A ***login shell*** is prompted when we log in to a machine via a console,
*for e.g.* remotely logging in a machine. In these circumstances
`.bash_profile` is executed to configure the shell before the initial
prompt.

But, if we are already logged in our machine and open a terminal
window (like *gnome-terminal*), then `.bashrc` is executed. `.bashrc` is also
executed when we start a new bash instance by typing `/bin/bash` in a
terminal.

---

We don't want to maintain two separate config files for *login* and
*non-login shells* because we don't want to write variables like `PATH`,
`JAVA_HOME` etc. in two places. We fix this by sourcing `.bashrc` from our
`.bash_profile`, then putting all the common settings in `.bashrc`.

To do this, we add the following lines to `.bash_profile` 


```bash
if [ -f ~/.bashrc ]; then
    source ~/.bashrc
fi
```
