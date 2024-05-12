### Task

The password for the next level is stored in a file called spaces in this filename located in the home directory.

### Connect to the remote machine

```
sshpass -f level2.pwd ssh bandit2@bandit.labs.overthewire.org -p 2220
```

### Solution

In order to handle spaces in a file name either the spaces need to be escaped or need to be double quoted.

```
cat ./spaces\ in\ this\ filename
```

```
cat ./"spaces in this filename"
```
