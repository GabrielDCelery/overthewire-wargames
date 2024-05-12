### Task

The password for the next level is stored somewhere on the server and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

### Connect to the remote machine

```
sshpass -f level6.pwd ssh bandit6@bandit.labs.overthewire.org -p 2220
```

### Solution

```
cd inhere
```

We need to use the find command from the `/` directory with a few filters to find the appropriate

- use the `-type f` flag to search for files
- use the `-user bandit7` flag to search for files owned by specific user
- use the `-group bandit6` flag to search for files owned by specific group
- use the `-size 33c` flag to specifiy the size of the file

Also there is the issue of permissions. When searching `/` we are usually running into the issue of files that we do not have access to shwing up as error as part of the output.

One way to solve that is to redirect the standard error channel using `2>/dev/null` or redirect to standard output then filter the results using grep `2>&1 | grep -v "Permission denied" | grep -v "No such file or directory")`.

```
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

This will give us the result

```
// OUTPUTS

/var/lib/dpkg/info/bandit7.password
```

```
cat /var/lib/dpkg/info/bandit7.password
```
