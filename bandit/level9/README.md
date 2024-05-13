### Task

The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

### Connect to the remote machine

```
sshpass -f level9.pwd ssh bandit9@bandit.labs.overthewire.org -p 2220
```

### Solution in detail

The command that helps to solve this problem is called `strings` which prints the sequences of printable characters in files. So if we use:

```
strings data.txt | grep =
```

then we get

```
// OUTPUTS

=2""L(
x]T========== theG)"
========== passwordk^
Y=xW
t%=q
========== is
4=}D3
{1\=
FC&=z
=Y!m
        $/2`)=Y
4_Q=\
MO=(
?=|J
WX=DA
{TbJ;=l
[=lI
========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
>8=6
=r=_
=uea
zl=4
```

Now the only problem is that the task does not specify how many `=` signs we are looking for, but since until now every password has been using the same pattern with `grep` and the correct flags and regular expression we can extract the password.

- use `-o` flag to only output the match
- use `-E` to use extended regexp

```
strings data.txt | grep = | grep -oE [A-Za-z0-9]{32}
```

### One line solution

```
strings data.txt | grep = | grep -oE [A-Za-z0-9]{32}
```
