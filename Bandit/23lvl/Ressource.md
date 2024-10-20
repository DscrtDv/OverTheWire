# Bandit Level 22 → Level 23
## Level Goal

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

*NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.
Commands you may need to solve this level*

> cron, crontab, crontab(5) (use “man 5 crontab” to access this)

### Solution

Here we discover a new hashing (encryption) algorithm MD5. After displaying the program and checking its permissions, we can run it on our own, and get the hash
for the filename of the password.

```
bandit22@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit23.sh 
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

bandit22@bandit:~$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:~$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
```