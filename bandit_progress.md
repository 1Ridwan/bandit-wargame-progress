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

