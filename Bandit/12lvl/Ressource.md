# Bandit Level 11 → Level 12
## Level Goal

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
Commands you may need to solve this level

> grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

### Solution
```
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m' | awk '{print $4}'
7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

translate the A-Z by 13.