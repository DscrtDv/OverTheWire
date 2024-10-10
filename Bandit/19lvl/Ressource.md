# Bandit Level 18 → Level 19
## Level Goal

The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.
Commands you may need to solve this level

> ssh, ls, cat


### Solution

Pretty straightforward, copy the file over ssh.

```
scp -P 2220 bandit18@bandit.labs.overthewire.org:readme .
cat readme
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```

