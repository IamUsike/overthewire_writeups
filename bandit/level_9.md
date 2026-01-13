**Task**
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

```
bandit8@bandit:~$ strings data.txt | sort | uniq -u
<<REDACTED>>
```

`-u` flag only displays unique lines and sort and uniq are self explanatory.
