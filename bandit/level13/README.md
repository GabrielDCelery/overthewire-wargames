### Task

The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on.

### Connect to the remote machine

```
sshpass -f level13.pwd ssh bandit13@bandit.labs.overthewire.org -p 2220
```

### Solution in detail

### One line solution
