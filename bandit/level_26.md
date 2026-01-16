**task**: Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

- you can find bandit26 ssh key in the home dir of bandit25

```
bandit25@bandit:~$ ls
bandit26.sshkey
```

- use that key to login (paste the key in your local mahine and `chmod 600`)

```
ssh bandit.labs.overthewire.org -p2220 -l "bandit26" -i bandit26.sshkey
```

we get logged out as soon as we login. Lets find out why this is happening

---

from bandit25 account.

- get the shell of bandit26

```
bandit25@bandit:~$ cat /etc/passwd | grep 26
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
```

```bash
bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
```

- set the terminal to linux
- print the contents on `text.txt` present in the home dir of the user executing it.

- the login shell script executes first when the user logs in.

eff I couldn't solve this.
here's a writeup :tear

[writeup](https://mayadevbe.me/posts/overthewire/bandit/level26/)
