# BANDIT 5 -> 6

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

    human-readable
    1033 bytes in size
    not executable

### Solution

bandit5@bandit:~/inhere$ du -hab | grep 1033 | awk '{print $2}' | xargs -I{} cat {} | tr -d "[:blank:]" 
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
bandit5@bandit:~/inhere$ 
```

- du -hab: list file size by *-h* human-readable, *-a* all (not just dir), -b in byte size
- grep 1033: filter by correct size
- awk '{print $2}': select second argument to previous command (filename)
- xarg -I{} cat {}: substitute result of previous command and use it as arg to cat
- tr -d "[:blank:]": removes white spaces from output