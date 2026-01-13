**Level Goal**

The password for the next level is stored somewhere on the server and has all of the following properties:

    owned by user bandit7
    owned by group bandit6
    33 bytes in size

```shell
bandit5@bandit:~$ find / -xdev -type f -user bandit7 -group bandit6 -size 33c  2>/dev/null
/var/lib/dpkg/info/bandit7.password
```

**explanation:**

- `find /` : Start the search from root dir
- `-xdev`: donot cross filesystem boundaries
- `type f`: look for files
- Then the user the file belongs to, the group and also the size
- `2>/dev/null`: redirect all errors to oblivion
