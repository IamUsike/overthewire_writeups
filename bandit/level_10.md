**TASK**: The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

The idea is to grep multiple equals to sign and some trailing lines from that point.

```shell
bandit9@bandit:~$ strings data.txt | grep "===" -A3
========== the
tWIN
W9`5
UnTZ
--
========== password
xw~{
^E[5
It~
--
f\Z'========== is
}b$9
Q^1"
1k3e
--
========== <<REDACTED>>
y'V's
4sV39
^s""
bandit9@bandit:~$

```
