# Bandit Level 15 → Level 16
## Level Goal

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

*Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.*

#### Commands you may need to solve this level

> ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss

### Research

OpenSSL comes with a client tool that you can use to connect to a secure server. The tool is similar to telnet or nc in the sense that it handles the encryption aspect but allows you to fully control the layer that comes next.

To connect to a server, you need to supply a hostname and a port. For example:

```
$ openssl s_client -crlf \
-connect www.feistyduck.com:443 \
-servername www.feistyduck.com
```

Notice that you had to supply the hostname twice. The -connect switch is used to establish the TCP connection, but -servername is used to specify the hostname sent at the TLS level. Starting with OpenSSL 1.1.1, the s_client tool automatically configures the latter. You’ll still need to use the -servername switch if (1) you’re using an earlier version of OpenSSL, (2) you’re connecting to an IP address, or (3) the TLS host needs to be different. Use the -noservername switch to avoid sending hostname information in the TLS handshake.

### Solution

```
openssl s_client -crlf /
-connect localhost:30001 /
-servername localhost /
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```