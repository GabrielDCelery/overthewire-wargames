### Task

The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

### Connect to the remote machine

```
sshpass -f level0.pwd ssh bandit0@bandit.labs.overthewire.org -p 2220
```

### Solution in detail

```
cat readme
```
