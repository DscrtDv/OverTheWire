# BANDIT lvl 6 -> 7

# Solution
```
find / -group bandit6 -user bandit7 2>/dev/null | xarfs -I{} cat {}
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

Filter find at root dir by user and group, and exclude the 
Permission denied by redirecting the STDERR to /dev/null.
Then use output to cat with xargs.