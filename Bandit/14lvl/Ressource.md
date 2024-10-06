# Bandit Level 13 → Level 14
## Level Goal

The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on
Commands you may need to solve this level

> ssh, telnet, nc, openssl, s_client, nmap
### Solution

You can copy the private key over ssh using scp

```
scp -P <port> <user>@<host>:<path_to_file> <destination_path>
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private . 
```
Once that is done you can attempt the connection on your own machine using ssh with -i flag, allowing the use of the private key to authenticate.
```
ssh -i <key> <user>@<host> -p <port>
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```
Although the server will notify the user that the permissions on the key are too open, other users can access it. To fix this:
```
chmod 600 <key>
```
We can now ssh into the next level and copy the password from:
```
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```


### Potential alternative
>An alternative to this method is starting a simple web server with python. This is useful when you do not have ssh access. On the machine where the file is you need to start the webserver with the following command: python3 -m http.server (best is to do it in the directory of the file). On the receiving machine you then just have to send an HTTP request: wget http://<ip>:8000/<pathtofile>