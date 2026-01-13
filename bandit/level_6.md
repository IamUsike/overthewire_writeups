**level goal**
Level Goal

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

    human-readable
    1033 bytes in size
    not executable

```shell
bandit5@bandit:~$ find ./inhere/ -type f -size 1033c ! -executable  -exec file {} + | grep -i ascii
./inhere/maybehere07/.file2: ASCII text, with very long lines (1000)
```

not in the mood to write command explanation look em up.
ps: can ignore `exec` and `grep` in here, you'll still get the single file.
