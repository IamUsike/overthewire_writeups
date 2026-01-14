**Task**: The password for the next level is stored in the file data.txt, which contains base64 encoded dat

- ssh into the machine

- decode the base64 text

```
bandit10@bandit:~$ base64 -d <<< cat data.txt
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```
