**Task** : The password for the next level is stored in a file called --spaces in this filename-- located in the home directory

- connect to ssh from the previously obtained password

```
ssh bandit.labs.overthewire.org -p2220 -l "bandit2"
```

We can find this by using the `find` command as done in level2 but since we have
an easier way

Quote from the stackoverflow answer from previous question

> This type of approach has a lot of misunderstanding because using - as an argument refers to STDIN/STDOUT i.e dev/stdin or dev/stdout .So if you want to open this type of file you have to specify the full location of the file such as ./- .For eg. , if you want to see what is in that file use `cat ./-`

<br>

final command will be

```
cat ./--spaces\ in\ this\ filename--
```
