How to see all the users present in a Linux installation.
===


In Linux `/etc/passwd` file contains one line entry separated by colons for
each account created in Linux. To see all the users we can just do -
```bash
$ cat /etc/passwd
```

This is the output that I got in this system -

```bash
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
games:x:12:100:games:/usr/games:/sbin/nologin
ftp:x:14:50:FTP User:/var/ftp:/sbin/nologin
nobody:x:99:99:Nobody:/:/sbin/nologin
avahi-autoipd:x:170:170:Avahi IPv4LL Stack:/var/lib/avahi-autoipd:/sbin/....
dbus:x:81:81:System message bus:/:/sbin/nologin
polkitd:x:999:999:User for polkitd:/:/sbin/nologin
abrt:x:173:173::/etc/abrt:/sbin/nologin
usbmuxd:x:113:113:usbmuxd user:/:/sbin/nologin
colord:x:998:998:User for colord:/var/lib/colord:/sbin/nologin
rtkit:x:172:172:RealtimeKit:/proc:/sbin/nologin
geoclue:x:997:996:User for geoclue:/var/lib/geoclue:/sbin/nologin
chrony:x:996:995::/var/lib/chrony:/sbin/nologin
tss:x:59:59:Account used by the trousers package to sandbox the tcsd
daemon:/dev/null:/sbin/nologin
unbound:x:995:994:Unbound DNS resolver:/etc/unbound:/sbin/nologin
openvpn:x:994:993:OpenVPN:/etc/openvpn:/sbin/nologin
avahi:x:70:70:Avahi mDNS/DNS-SD Stack:/var/run/avahi-daemon:/sbin/nologin
pulse:x:993:991:PulseAudio System Daemon:/var/run/pulse:/sbin/nologin
gdm:x:42:42::/var/lib/gdm:/sbin/nologin
gnome-initial-setup:x:992:989::/run/gnome-initial-setup/:/sbin/nologin
nm-openconnect:x:991:988:NetworkManager user for OpenConnect:/:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
vyadav:x:1000:1000:Vishal Yadav:/home/vyadav:/bin/bash
lightdm:x:990:986::/var/lib/lightdm:/sbin/nologin
postgres:x:26:26:PostgreSQL Server:/var/lib/pgsql:/bin/bash
apache:x:48:48:Apache:/usr/share/httpd:/sbin/nologin
```

Other ways that can be used are -
```bash
$ more /etc/passwd
$ less /etc/passwd
```

One might wonder, why are there so many entries in the `/etc/passwd`, when the
number of users created is relatively small? Does my system contain so many
users?

*Well*, the answer to this is ***yes***.

##### But I have never created so many users!!!!

These other entries are system generated for the programs that are used for
day to day functioning of the Linux, and similar entries can be found in almost
all types of Linux distributions.

Now lets understand the information corresponding to a single user which is
present in a single line. Lets take the following example:

    vyadav:x:1000:1000:Vishal Yadav:/home/vyadav:/bin/bash
    ------ - ---- ---- ------------ ------------ ---------
      |    |   |    |        |            |          |
      1    2   3    4        5            6          7
    
    1) Username: It is used when user logs in. It should be between 1-32
    characters long.
    2) Password: An 'x' character indicates that encrypted password is stored in
    /etc/shadow file.
    3) User ID (UID): Each user is assigned a user ID (UID). UID 0 is reserved
    for root and UIDs 1-99 are reserved for other predefined accounts. Further
    UID 100-999 are reserved by system for administrative and system
    accounts/groups.
    4) Group ID (GID): The primary group ID (stored in /etc/group file)
    5) User ID Info: The comment field. It allows you to add extra information
    about the users such as user's full name, phone number etc. This field is
    used by 'finger' command.
    6) Home Directory: The absolute path to the directory the user will be in
    when they log in. If this directory does not exist, then users' directory
    becomes /.
    7) Command/Shell: The absolute path of a command or shell (/bin/bash).
    Typically, this is a shell. Please note that it does not have to be a shell.
    
