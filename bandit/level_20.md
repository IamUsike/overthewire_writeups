**task**: To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

- suid lets us run commands as the user who owns that file

```
#execute the file
bandit19@bandit:~$ ./bandit20-do
Run a command as another user.
  Example: ./bandit20-do whoami

#We are the user bandit20 so we can directly print his password from the pw dir
bandit19@bandit:~$ ./bandit20-do whoami
bandit20

#cat the pw
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
<<REDACTED>>
```
