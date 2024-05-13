### Task

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

### Connect to the remote machine

```
sshpass -f level8.pwd ssh bandit8@bandit.labs.overthewire.org -p 2220
```

### Solution

The tool to solve these types of issues (duplicate lines) is the `uniq` command. Before using it we need to sort the lines to make sure the passwords that have multiple occurrences are next to each other.

```
cat data.txt | sort | uniq -u
```
