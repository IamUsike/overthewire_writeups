**task**: There is a git repository at ssh://bandit28-git@bandit.labs.overthewire.org/home/bandit28-git/repo via the port 2220. The password for the user bandit28-git is the same as for the user bandit28.

- initially when we clone the repo using <br>
  `git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo`

  the password is shown as a bunch of 'x'

- since this is version contolled and tracked. do `git log` to see the commit history.
![[Pasted image 20260116125631.png]]

looking at the commit history, we can see that the comment on the latest commit says `fix info leak`. So, presumably the previous commit should contain the creds. (you can just checkout all the commits smh)

- `git checkout 8b7c651b37ce7a94633b7b7b7c980ded19a16e4f`

Inspect the readme file now to get the password for the next level. 