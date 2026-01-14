**Task**: The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed

- ssh into the server

```
ssh bandit.labs.overthewire.org -p2220 -l "bandit12"
<<password from prev challenge>>
```

```
# given data.txt is a hexdump of a compressed archive so
#Revert a plaintext hexdump back into binary, and save it as a binary file
bandit12@bandit:~$ xxd -r data.txt > /tmp/reverted_file

#get the file type of the new file
bandit12@bandit:~$ file /tmp/reverted_file
/tmp/reverted_file: gzip compressed data, was "data2.bin", last modified: Tue Oct 14 09:26:06 2025, max compression, from Unix, original size modulo 2^32 564
```

- Since the _reverted_file_ is a gzip compressed data can be extracted by using
  `gzip -d` or `gunzip`. `gzip -d` will throw the following error as it needs the suffix to be gz(double check this plis).

```shell
bandit12@bandit:~$ gzip -d /tmp/reverted_file
gzip: /tmp/reverted_file: unknown suffix -- ignored

```

- The above error can be solved by either adding the `.gz` suffix or by using `gunzip` directly. Find both methods below

```shell
#adding the suffix
bandit12@bandit:/tmp$ mv reverted_file reverted_file.gz
bandit12@bandit:/tmp$ gzip -d reverted_file.gz

bandit12@bandit:/tmp$ file reverted_file
reverted_file: bzip2 compressed data, block size = 900k
```

```shell
#using gunzip
bandit12@bandit:~$ gunzip -c /tmp/reverted_file > /tmp/extracted
bandit12@bandit:~$ file /tmp/extracted
/tmp/extracted: bzip2 compressed data, block size = 900k

```

- Extract the bzip2 archive now
- `-d` is used to decompress
- `-k` to preserve the original archive

```
bandit12@bandit:~$ bzip2 -dk /tmp/extracted
bzip2: Can't guess original name for /tmp/extracted -- using /tmp/extracted.out
bandit12@bandit:~$ file /tmp/extracted.out

/tmp/extracted.out: gzip compressed data, was "data4.bin", last modified: Tue Oct 14 09:26:06 2025, max compression, from Unix, original size modulo 2^32 20480

```

- once again its a gzip archive

```shell
bandit12@bandit:~$ gunzip -c /tmp/extracted.out > /tmp/gz_extract

bandit12@bandit:~$ file /tmp/gz_extract
/tmp/gz_extract: POSIX tar archive (GNU)
```

- for no particular reason <br>
  `mv gz_extract gz_extract.tar`

- Now, to extract the tar archive (notice the `pwd` is now `/tmp` since there in no
  write perms at `~`) | _ofc I could write to tmp without moving there_

- `-x`: extract
- `-v`: verbose
- `-f`: name of the input file

```
bandit12@bandit:/tmp$ tar -xvf /tmp/gz_extract.tar
data5.bin

bandit12@bandit:/tmp$ file data5.bin
data5.bin: POSIX tar archive (GNU)

bandit12@bandit:/tmp$ tar -xvf /tmp/data5.bin
data6.bin

bandit12@bandit:/tmp$ tar -xvf /tmp/data6.bin
data8.bin

bandit12@bandit:/tmp$ tar -xvf /tmp/data8.bin

bandit12@bandit:/tmp$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Tue Oct 14 09:26:06 2025, max compression, from Unix, original size modulo 2^32 49
```

- extract the gzip archive

```
bandit12@bandit:/tmp$ gunzip -c data8.bin > /tmp/data8

bandit12@bandit:/tmp$ file data8
data8: ASCII text

bandit12@bandit:/tmp$ cat data8
The password is <<REDACTED>>

```
