# Bandit Level 9 → Level 10
## Level Goal

The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.
Commands you may need to solve this level

> grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

### Solution
```
bandit9@bandit:~$ strings data.txt | grep ==
}========== the
3JprD========== passwordi
~fDV3========== is
D9========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
bandit9@bandit:~$ 

```

Could be cleaner, but it does the job. Strings will print readable char sequences in files.
Filter by "several" equals signs. Several is more than one, it is then enough to get the correct output.