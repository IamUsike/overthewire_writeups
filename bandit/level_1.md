Task: Requires to find the password for `bandit1` from a readme file
located in the current users home dir

```
#change into the users home dir
cd ~

#list all the files in the pwd
ls (the output shows a readme file)

#print the readme file
cat readme
```

Copy the password and ssh into the server with username _bandit1_

`ssh bandit.labs.overthewire.org -p2220 -l "bandit1"`
