The password for the next level is stored in a file called - located in the home directory

- Go to the user's home dir
  `cd ~`

- list the files in the pwd

```
bandit1@bandit:~$ ls
-
```

since `-` is a special character (used to toggle between previously visited dirs)
we cant directly do `cat -`

Oh, `cat -` is an explicitly defined behavior which means "read from stdin and print
to stdout"

I did this by recursively printing all the files (by running find)
`find . -type f ! -name "*bash*"  -exec cat {} \;`

---

ps: If we go to the helpful reading materials in the website you can find an easier
way to do this.

[This](https://stackoverflow.com/questions/42187323/how-to-open-a-dashed-filename-using-terminal) is one such way
