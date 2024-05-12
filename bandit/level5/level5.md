### Task

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

### Connect to the remote machine

```
sshpass -f level5.pwd ssh bandit5@bandit.labs.overthewire.org -p 2220
```

### Solution

```
cd inhere
```

We need to use the find command with a few filters to find the appropriate file

- use the `-type f` flag to search for files
- use `-size 1033c` flag to specifiy the size of the file
- use `! -executable` flag (which is a negated one) to search for non-executable

```
find . -type f -size 1033c ! -executable
```

This will give us

```
// OUTPUTS

./maybehere07/.file2
```

Then we can use the `file` command to verify if it is human readable.

```
file ./maybehere07/.file2
```

```
// OUTPUTS

./maybehere07/.file2: ASCII text, with very long lines (1000)
```

```
cat ./maybehere07/.file2
```

Or again if you want to handle it in a single line

```
cat $(file $(find . -type f -size 1033c ! -executable) | grep ASCII | cut -d ":" -f1)
```
