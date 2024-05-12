### Task

The password for the next level is stored in a file called - located in the home directory.

### Connect to the remote machine

```
sshpass -f level1.pwd ssh bandit1@bandit.labs.overthewire.org -p 2220
```

### Solution

The tricky part about this challenge is that `-` is the standard option character. Most of the commands on Linux treat the string `-` as a synonym for stdin or stdout.

So if we were to use `cat -` it would read from stdin.

The solution is either to use the full path to the file

```
cat ./-
```

or to redirect the input from the file to cat

```
cat < -
```
