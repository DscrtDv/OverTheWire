# Bandit Level 17 → Level 18
## Level Goal

There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

*NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19
Commands you may need to solve this level*

> cat, grep, ls, diff


### Solution

```
bandit17@bandit:~$ diff passwords.new passwords.old 
42c42
< x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
---
> ktfgBvpMzWKR5ENj26IbLGSblgUG9CzB
bandit17@bandit:~$
```

The first line of the diff output contains:

- line numbers corresponding to the first file,
- a letter (a for add, c for change, or d for delete), and
- line numbers corresponding to the second file.

- Lines preceded by a < are lines from the first file;
- lines preceded by > are lines from the second file.

The three dashes ("---") merely separate the lines of file 1 and file 2.

Meaning our password is:
```
x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```