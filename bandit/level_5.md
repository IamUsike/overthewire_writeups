**Level Goal**

The password for the next level is stored in the only human-readable file in the inhere directory.

- ssh into the server using the password found in the previous challenge(username `bandit4`)

```shell
#list pwd
bandit4@bandit:~$ ls
inhere

#list all in the inhere dir
bandit4@bandit:~$ la inhere/
-file00  -file02  -file04  -file06  -file08
-file01  -file03  -file05  -file07  -file09

#find the file type of all the files in the inhere directory
bandit4@bandit:~$ file inhere/*
inhere/-file00: data
inhere/-file01: OpenPGP Public Key
inhere/-file02: OpenPGP Public Key
inhere/-file03: data
inhere/-file04: data
inhere/-file05: data
inhere/-file06: data
inhere/-file07: ASCII text
inhere/-file08: data
inhere/-file09: data

#the description mentions that the password is stored in the only human
#human-readable file.
bandit4@bandit:~$ cat ./inhere/-file07
<snip>

```
