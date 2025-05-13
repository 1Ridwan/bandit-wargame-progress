## Level 0 → Level 1

### Goal:
SSH into bandit0@bandit.labs.overthewire.org on port 2220

### Commands Used:
```bash
ls
cat readme

## Level 1 -> Level 2

### Goal:
Read a file with a filename that includes a special character '-'

### Commands Used
```bash
ls
cat ./-

# Level 2 -> Level 3

### Goal:
Read a file with a filename that includes spaces

### Commands Used
```bash
ls
cat spaces\ in\ this\ filename

# Level 3 -> Level 4

### Goal:
Read a hidden file

### Commands Used
```bash
ls
cd inhere
ls
ls -a
cat ...Hiding-From-You

# Level 4 -> Level 5

### Goal:
Find the human readable file

### Commands Used
```bash
ls
cd inhere
ls
find . -exec file {} \;


## I struggled with this one, but I learnt what human readable files mean now
## Also learnt how to use '-exec file {} \;' which seems like it will be really useful in the future!


# Level 5 -> Level 6

### Goal:
Find the file that is human-readable, 1033 bytes in size, and not executable

### Commands Used
```bash
ls
cd inhere
ls
ind . -size 1033c
cat ./maybehere07/.file2

## Feel like i took the easy route as i only checked for files that were 1033 bytes in size... 


# Level 6 -> Level 7

### Goal:
Find the file in the server that has 3 different properties

### Commands Used
```bash
ls
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password



## This one was difficult at first. I knew how to search for files using filters. I initially ran 
find . -type f -user bandit7 -group bandit6 -size 33c
## But this wasn't working, and i kept seeing permission denied messages that were just distracting... Which is when i discovered 2>/dev/null to hide error messages
## Then i realised 'find .' only searches the current directory tree, whereas 'find /' searches the entire file system, starting at the root and then searching every directory!
## using 'find /' is very slow, so its essential to use filters!

