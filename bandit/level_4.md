**Level Goal**

The password for the next level is stored in a hidden file in the inhere directory.

- ssh into the server with the password found in the previous level

```
#list all files in the pwd
bandit3@bandit:~$ la
.bash_logout  .bashrc  inhere  .profile

#print the password
bandit3@bandit:~$ cat inhere/...Hiding-From-You
<snip>

```
