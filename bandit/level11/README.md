### Task

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

### Connect to the remote machine

```
sshpass -f level11.pwd ssh bandit11@bandit.labs.overthewire.org -p 2220
```

### Solution in detail

The problem can be solved with the `tr` command that allows for simple character transformations that also work on ranges of characters.

Since the latin alphabet is 26 characters long that means when we specify a range of characters FROM whoch we want to transorm the TO range of characters is made up of the rest of the characters. Example `a-m` -> `n-z` or `n-z` -> `a-m`. And we have to do the same for upper case characters as well.

```
cat data.txt | tr 'A-M N-Z a-m n-z' 'N-Z A-M n-z a-m'
```

and we get the password

```
// OUTPUTS

The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
```

### One line solution

```
cat data.txt | tr 'A-M N-Z a-m n-z' 'N-Z A-M n-z a-m' | grep -oE [a-zA-Z0-9]{32}
```
