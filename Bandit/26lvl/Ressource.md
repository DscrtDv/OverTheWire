# Bandit Level 25 → Level 26
## Level Goal

Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

**NOTE: if you’re a Windows user and typically use Powershell to ssh into bandit: Powershell is known to cause issues with the intended solution to this level. You should use command prompt instead.**

> Commands you may need to solve this level
> ssh, cat, more, vi, ls, id, pwd

### Solution
The *more* command allows us to display text file in interactive mode. This can only occur when the file contains large text. This will come in handy, but first we need to figure the default shell.
```
grep "bandit26" /etc/passwd
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
```
We can see the default shell is "showtext" which seems to be executing a script that cats a text file when attempting to connect to bandit26. Hence, if we reduce the terminal window enough, the text will be large enough for more to enter in interactive mode. Once that is set, we can type 'v' to enter vim. We now only have to change the default shell and invoque it.

```
:set shell=/bin/bash
:shell
upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB
```