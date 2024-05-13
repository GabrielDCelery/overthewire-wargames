### Task

The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on.

### Connect to the remote machine

```
sshpass -f level13.pwd ssh bandit13@bandit.labs.overthewire.org -p 2220
```

### Solution in detail

After logging into the server in the home directory there is a privae SSH key that identifies `bandit14`. First we have to copy that from the remote machine to our local machine

```
sshpass -f level13.pwd scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
```

If we try to use the key immediately we will get an error `Permissions 0640 for 'sshkey.private' are too open` so first we need to change the permission of the key.

```
chmod 700 sshkey.private
```

then login

```
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

and the password is located in the file specified in the description section.

```
cat /etc/bandit_pass/bandit14
```

### One line solution
