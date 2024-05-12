### Task

The password for the next level is stored in a hidden file in the inhere directory.

### Connect to the remote machine

```
sshpass -f level3.pwd ssh bandit3@bandit.labs.overthewire.org -p 2220
```

### Solution

First we need to enter the directory that stores the hidden file and list the hidden files to get the file name.

```
cd inhere
ls -la
```

The above commands will show you the name of the hidden file with the `.` prefix.

```
// OUTPUTS

drwxr-xr-x 2 root    root    4096 Oct  5  2023 .
drwxr-xr-x 3 root    root    4096 Oct  5  2023 ..
-rw-r----- 1 bandit4 bandit3   33 Oct  5  2023 .hidden
```

```
cat .hidden
```
