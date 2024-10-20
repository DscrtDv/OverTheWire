# Bandit Level 20 → Level 21

## Level Goal

There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

*NOTE: Try connecting to your own network daemon to see if it works as you think*
Commands you may need to solve this level

> ssh, nc, cat, bash, screen, tmux, Unix ‘job control’ (bg, fg, jobs, &, CTRL-Z, …)

### Solution

Interesting level. I still struggle getting a gist of those setuid binary file, but I'll figure it out.
We need to run two processes. We cannot really divide the termminal, but we can use screen to start what I would call a "virtual session".
From the man:

> Screen  is  a  full-screen window manager that multiplexes a physical terminal between several processes (typically interactive  shells).

This is important, because once screen launched we can start new shell processes within it and split windows. This will allow us to run different programs in the same sessions
without terminating them.

```
screen
C-a c 		(create a new window with terminal)
C-a | 		(split)
C-a TAB 	(jump to next area)
C-a digit 	(select window)
```

Once we have that set up we can connect to our "network daemon using nc
```
netcat -l localhost 12345
(switch window)
./suconnect 12345
```
Note that the port is arbitrary. The -l flag allows for "listening".
We can now run our setuid executable in the other window, submit the current password to nc
and voila!

```
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
```
