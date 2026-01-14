**task**: There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

- idk why this isnt working

```
join -v 2 passwords.old passwords.new
```

- We can use the command `diff` which compares files line by line to get the answer

```
bandit17@bandit:~$ diff passwords.old  passwords.new
42c42
< pGozC8kOHLkBMOaL0ICPvLV1IjQ5F1VA
---
> << REDACTED >>
```
