`su` and `sudo` in Linux
====

`root` user has access to all the commands and files on Linux. Both `su`
and `sudo` are used to run commands with root permissions. Normal users on
Linux run with reduced permissions - e.g. they can't install software.

## The `su` command


`su` stands for **Substitute user**. `su` is used to run a command with
substitute user.

When we do something like  `su vyadav`, it prompts for a password for the 
user `vyadav`. After the password is entered, the shell
will switch to `vyadav's` user account.

If we do not give any `username` as an argument it will switch to
`root` users' account.


## The `sudo` command

`sudo` allows us to execute a command *(that means only 1 command)* as
another user.

Suppose if you want to install a package, you can use `sudo` as -
```bash 
sudo apt-get install <package-name>
```
 
This would be run; and after the command is executed, you will go back to your original user.


## Difference between `su` and `sudo`


`su` switches you to the *root* user account and requires the *root*
account's password.

`sudo` runs a single command with root privileges, it does ***NOT*** switch
to the `root` user or require a separate `root` user password.


### Ubuntu vs Other Linux Distributions

`su` command is the traditional way of acquiring *root* permissions on
Linux.

The `sudo` command existed for a long time. Ubuntu uses `sudo`-only
by default. When we install Ubuntu, the standard *root* account ***IS*** created,
but *no password is assigned to it*. We can't log in as *root* until we
assign a password to the root account. We do that by -
```bash
sudo passwd root
```

There are several advantages to using `sudo` instead of `su` by
default. Ubuntu users only have to provide and remember a *single password*,
whereas Fedora requires us to create *separate root and user account
passwords during installation*.

In Ubuntu, the users who have the `sudo` access are stored in *sudoers
file*. So if we want to have more users who have `sudo` access, we either

1. add them using -
    ```bash
    sudo adduser <username> admin
    ```

2. make an entry in the ***sudoers*** file `/etc/sudoers`


### Fedora and `su`

Fedora, unlike Ubuntu, requires a user to create a `su` password for
*root* account. In Ubuntu only the account is created and no password is
assigned.

In Fedora the *root* password is set *during installation*. We can
change the *root* password using the `passwd` utility. These are the steps
to be followed -

1. Open a terminal and change to root user.
   ```bash
   su -
   <password>
   ```
   We are then switched to the root user.
    
2. Then we can change the password the same way we would change any
   other password, using `passwd` - 
   ```bash
   passwd root
   <password>
   ```
    

When `su` is used by administrators they should use hypen(`-`) along
with `su`. There are 2 major uses of hypen(`-`) symbol are - 

1. It switches the current directory to the home directory of the new user.
2. It changes the environmental variables to those of the new user.

Thus, if we enter the command -
`su - vyadav` (A user `vyadav` with home directory `/home/vyadav`)
The shell switches to the user `vyadav` and the current working directory
becomes `/home/vyadav` and the *environmental variables* of the user are 
set to those specified by the `vyadav`'s `.bashrc` or `.bash_profile`.

Just as we add new users to *sudoers*, we can also create extra *root*
user account with `su` in Fedora.

1. `adduser -u 0 -o -g 0 -G 0 -M <username>`
2. `passwd <username>`
Then see the id created using - `id <username>`.
[See More](http://www.labtestproject.com/create_root_user_account)


---

#### Tips and Tricks

##### Using 'su' like 'sudo'
 
To run a single command as the *root* user with `su`, use the following
command:

```bash
su -c 'command'
```

##### To get an interactive *root* shell for `sudo`
 
`sudo` lets us execute only **ONE** command as a *root*, but if we want a
full interactive shell with `sudo`, we can use:

```bash
sudo -i
```

