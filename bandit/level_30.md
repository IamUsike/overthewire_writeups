**task**: There is a git repository at ssh://bandit29-git@bandit.labs.overthewire.org/home/bandit29-git/repo via the port 2220. The password for the user bandit29-git is the same as for the user bandit29.

- clone the repo

```
wofo@kitetsu ~/Documents/dumbShi/test $ git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
```

okay man I'm too cool for ts (waiting to get humbled)

- the readme says `no passwors in prod`. This indicates the possibilities of other branches existing.

- list all branches using `git branch -a`

- there'll be a dev branch switch to it and get the pw
  `git checkout dev`
