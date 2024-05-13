### Task

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

### Connect to the remote machine

```
sshpass -f level4.pwd ssh bandit4@bandit.labs.overthewire.org -p 2220
```

### Solution in detail

```
cd inhere
```

The way you can identify a human readable file is by using the `file` command.

```
file ./*
```

Among the results the one that says `ASCII text` is the one we are looking for

```
// OUTPUTS

./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```

```
cat ./-file07
```

Or if you want to do it using a one liner.

```
cat < $(file ./* | grep ASCII | cut -d ':' -f1)
```
