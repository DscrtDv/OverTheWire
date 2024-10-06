# BANDIT 4 -> 5

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

### Solution

> the *file* command allows to check file types. We select all file with ./-* and filter by the string ASCII.

```
bandit4@bandit:~/inhere$ file ./-* | grep ASCII
./-file07: ASCII text
bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
bandit4@bandit:~/inhere$ 
```