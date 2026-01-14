**task**: The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

- use scp to fetch the readme file
- sample usage can be found [here](https://www.reddit.com/r/linux4noobs/comments/189ez4c/trying_to_send_a_file_with_scp/)

```shell
wofo@kitetsu ~/Documents/dumbShi/test $ scp -P 2220 -i sshkey.private bandit18@bandit.labs.overthewire.org:/home/bandit18/readme .


backend: gibson-1
bandit18@bandit.labs.overthewire.org's password:
readme                                                                  100%   33     0.1KB/s   00:00

```
