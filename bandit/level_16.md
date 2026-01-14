**task**: The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

- nmap scan (version enum is taking forever for some reason)

```shell
bandit15@bandit:~$ nmap localhost -p30001
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-01-14 06:41 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00013s latency).

PORT      STATE SERVICE
30001/tcp open  pago-services1

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
```

- connect using `s_client`

```
bandit15@bandit:~$ openssl s_client -connect localhost:30001
CONNECTED(00000003)
<SNIP>.....................
read R BLOCK
<<PASTE PASSWORD OF BANDIT15>>
Correct!
<BANDIT16 PASSWORD>>

closed

```
