**task**: There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

- listen on `netcat` and then send the password of bandit20 upon connection

```shell
echo "0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO" | nc -l -p 5000
<<  REDACTED >>
```

- upon executing the script the next password will be sent
