### Task

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!).

### Connect to the remote machine

```
sshpass -f level12.pwd ssh bandit12@bandit.labs.overthewire.org -p 2220
```

### Solution in detail

This task is quite a tedious one. First let's create a temporary folder and copy the hexdump file as instructed.

```
cd /tmp
cd $(mktemp -d)
cp /home/bandit12/data.txt ./hexdump0
```

After that we will have to use the `xxd` command to convert the hex dump back to binary that can be decompressed. In order to be able to tell what was the format of the compression we can use a concept called [file signatures](https://en.wikipedia.org/wiki/List_of_file_signatures) which means some file formats can be identified using the starting hexadecimals of the hex dump.

```
cat hexdump0 | head
```

```
// OUTPUTS
00000000: 1f8b 0808 0650 b45e 0203 6461 7461 322e  .....P.^..data2.
00000010: 6269 6e00 013d 02c2 fd42 5a68 3931 4159  bin..=...BZh91AY
00000020: 2653 598e 4f1c c800 001e 7fff fbf9 7fda  &SY.O...........
```

From `1f8b` we can tell that it is a gzip file so we can convert the hex dump to the appropriate binary format.

```
xxd -r hexdump0 compressed0.gz
```

Then decompress it using gzip

```
gzip -d compressed0.gz
```

We repeat the above steps until we reach the point that we see `data5.bin` in the hex dump which is an actual file (so now we are at the point where we got a `tar` archive). Renamed the tarfile to `archive.tar` and then extracted its contents.

```
tar -xf archive.tar
```

Then we keep repeating the aboe tasks until we reach the password.

### One line solution
