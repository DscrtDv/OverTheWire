# Bandit Level 12 → Level 13
## Level Goal

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)
Commands you may need to solve this level

> grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv, file

### Solution

According to the gzip format specification

>RFC 1952             GZIP File Format Specification             May 1996


      2.3.1. Member header and trailer

         ID1 (IDentification 1)
         ID2 (IDentification 2)
            These have the fixed values ID1 = 31 (0x1f, \037), ID2 = 139
            (0x8b, \213), to identify the file as being in gzip format.
Gzip files can be identfied with signature 1f8b.
Now that we know that, we can revert the file to binary, and decompress it using gzip.
After doing so, I tried to use gzip twice on the file, and "not a gzip format" error was thrown.
> bzip2 (.bz2) starts with 0x42, 0x5a, 0x68
Hex dump again using xxd.
Once again after observing the format specification, The format turns to be bzip2.
After decompressing again, the new format is gzip again.

# Second try

Using file will attempt to fetch the signature from the header and print which compression algo was used.

using that over and over allows to figure each file type until the password is revealed.
```
data8.bin: cannot open `data8.bin' (No such file or directory)
bandit12@bandit:/tmp/tmp.D0oYn8eTxa$ file 8.bin 
8.bin: gzip compressed data, was "data9.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 49
bandit12@bandit:/tmp/tmp.D0oYn8eTxa$ cat 8.bin | gzip -d > 9.bin
bandit12@bandit:/tmp/tmp.D0oYn8eTxa$ cat 9.bin 
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

```
