# Bandit Level 16 → Level 17
## Level Goal

The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

*Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.
Commands you may need to solve this level*

> ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss

### Solution
Supposedely this should scan in the correct range added with the -sV flag enabling service detection. Although nmap seems to have a hard time.
```
nmap -sV localhost -p 31000-32000
```

SO i settle for this:
```
nmap localhost -p 31000-32000
openssl s_client -ign_eof -connect localhost:31790
private.key retrieved
```