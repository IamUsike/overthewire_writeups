**task**: A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.
You do not need to create new connections each time

- tldr: get all the passwords (4 digit chars) in a file. And pass it to `nc` and save the
  stdout to a file and then `grep -v Wrong`

```
#change to a tempdir
cd $(mktemp -d)
```

````bash
# all 4 digit numbers
for i in {0..9}{0..9}{0..9}{0..9}; do
  echo "<bandit24_password> $i"
done > pw.txt
```

```bash
cat pw.txt | nc localhost 30002 >> results.txt
```

```bash
grep -v -i wrong results.txt
```

````
