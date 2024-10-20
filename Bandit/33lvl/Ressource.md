# Bandit Level 32 → Level 33
## Level Goal

After all this git stuff, it’s time for another escape. Good luck!
Commands you may need to solve this level

> sh, man

### Solution

the *$0* expension allows us to break out of the uppershell and cat the pswd.
```
$ cat /etc/bandit_pass/bandit33
tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0
```

$0 expands to /bin/bash hence, it is like calling a new shell.