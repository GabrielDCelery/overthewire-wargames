### Task

The password for the next level is stored in the file data.txt next to the word millionth.

### Connect to the remote machine

```
sshpass -f level7.pwd ssh bandit7@bandit.labs.overthewire.org -p 2220
```

### Solution in detail

One liner:

```
cat data.txt | grep millionth | sed -E "s/\s+/\ /g" | cut -d " " -f2
```
