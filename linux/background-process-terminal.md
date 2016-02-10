Starting and killing a background process in Linux Terminal
===

Many a times, we want to start a command from Terminal
but detach it from the shell so that we can still use the shell.

#### Start the background process

To start a process in background in the Terminal use -
```bash
<command> &
```

This starts the process without the shell getting blocked and you can
use it for further processing.

There is a problem with this though. We can still see some output by the `<command>`.

*for e.g.* If we start VLC using - `vlc &`, there are some logs
shown in the terminal output. 

To remove these we can use another similar command
```bash
(nohup <command> 2>/dev/null &)
```
**OR**
```bash
<command> > /dev/null 2>&1 &
```

#### Stop/Kill the background process

To **stop/kill** the same process using `kill` we can do this -

```bash
kill `ps -C <command> -o pid=`
```

**OR**

we can see the process id of the process when the command is run
*for e.g.*
```bash
vishal@vishal-ThinkPad-T540p:~$ vlc > /dev/null 2>&1 &
[1] 14754
```

and use this process ID (here 14754) and give a simple `kill` command.
```bash
kill -9 14754
```

(for more details of this particular `ps` command see *man-page* of `ps`)