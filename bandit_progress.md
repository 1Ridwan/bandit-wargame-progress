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
