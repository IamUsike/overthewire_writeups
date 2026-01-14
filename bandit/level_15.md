**task**: The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

- Get the password of the current user.
- The path can be found from the previous challenge

```
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
<<REDACTED>>
```

- The service on that particular port

```
bandit14@bandit:~$ nmap localhost -p30000
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-01-14 06:20 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00013s latency).

PORT      STATE SERVICE
30000/tcp open  ndmps

```

- connect to port 3000 using nc and paste the password of bandit14

```shell
bandit14@bandit:~$ nc localhost 30000
<<BANDIT14 PASSWORD>>
Correct!
<<BANDIT15 PASSWORD>>

```
