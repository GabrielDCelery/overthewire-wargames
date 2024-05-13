### Task

The password for the next level is stored in the file data.txt, which contains base64 encoded data.

### Connect to the remote machine

```
sshpass -f level10.pwd ssh bandit10@bandit.labs.overthewire.org -p 2220
```

### Solution in detail

There is a command to base64 encode files or standard input.

```
cat data.txt | base64 -d
```

which gives

```
// OUTPUTS

The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
```

### One line solution

```
cat data.txt | base64 -d | grep -oE [A-Za-z0-9]{32}
```
