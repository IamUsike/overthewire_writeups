**Task**: The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Look at the commands that logged you into previous bandit levels, and find out how to use the key for this level.

- A relatively easier challenge.

-list the contents of the pwd

```
bandit13@bandit:~$ ls -al
total 24
drwxr-xr-x   2 root     root     4096 Oct 14 09:26 .
drwxr-xr-x 150 root     root     4096 Oct 14 09:29 ..
-rw-r--r--   1 root     root      220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root     root     3851 Oct 14 09:19 .bashrc
-rw-r--r--   1 root     root      807 Mar 31  2024 .profile
-rw-r-----   1 bandit14 bandit13 1679 Oct 14 09:26 sshkey.private

```

- copy the private key and paste it into your local machine.
- And then in your local machine

```
## set proper perms
wofo@kitetsu ~/Documents/dumbShi/test $ chmod 600 sshkey.private

wofo@kitetsu ~/Documents/dumbShi/test $ l
.rw------- wofo users 1.6 KB Wed Jan 14 11:40:04 2026  sshkey.private

# -i flag to specify the private key
wofo@kitetsu ~/Documents/dumbShi/test $ ssh bandit.labs.overthewire.org -p2220 -l "bandit14" -i sshkey.private

```
