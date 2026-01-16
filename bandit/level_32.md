:tear not one more git

**task**: There is a git repository at ssh://bandit31-git@bandit.labs.overthewire.org/home/bandit31-git/repo via the port 2220. The password for the user bandit31-git is the same as for the user bandit31.

- the readme file contains the following

```
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
```

- do `ls -la` and you'll see a `.gitignore` file (look up what they mean) with
  `*.txt` ie; wont push the files ending with `.txt` to remote.

- either remove the gitignore file or remove the entry in it

- create a `keys.txt` with content mentioned in readme and then

from root

```
git add .
git commit -m "add key"
git push origin master
```

- you should get the password after this
