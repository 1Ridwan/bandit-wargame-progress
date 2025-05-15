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



# Level 7 -> 8

### Goal:
Find the password next to a specific word

### Commands Used
```bash
ls
rep -i 'millionth' data.txt

##Initially tried to use the find command which didn't work
## Remembered that grep lets me search for words, used -i to ignore case



# Level 8 -> 9

### Goal:
Find the line of text that occurs only once

### Commands Used
```bash
ls
sort data.txt | uniq -c | grep '1 '

## Initially did 
sort data.txt | uniq
## however this returned a huge block of text that i didnt understand so i used 
sort data.txt | uniq -c 
## now i had the total count for each line, but it was still a huge block of text so i used grep to return the line that only appears once!

## Level 9 -> 10

## Goal: Find password in one of the few human readable strings, preceded by several '='

### Commands Used
```bash
strings data.txt | grep "==="

## Found this much easier, i realised
strings data.txt
## returned all human readable lines in the file, so i used grep to finish the job  


## Level 10 -> 11

## Goal: Find password in file which contains base64 data

### Commands Used
```bash
base64 data.txt -d

## Super easy, looked at the manual for base64 and realised base64 -d would decode the data


## Level 11 -> 12

## Goal: Find password in file which has ROT13 applied

### Commands Used
```bash
tr 'A-Za-z' 'N-ZA-Mn-za-m' <<< 'Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4'

  
## Had no clue at first, i knew how to do this in python from previous experience
## decided to look at the helpful reading material and learn how to use the tr command

## UPDATE
## Went through the whole game again and realised i can use 
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m' 
## instead, this is a better command as it can be used in a script
## will always work even if the contents of data.txt change
## doesnt require me to cat data.txt first to see the contents





# Level 12 -> 13

## Goal: Find password in file that has been repeatedly compressed

### Commands Used
```bash
mv
cp
gzip -d
bzip2 -d
mktemp -d
file

## This level was insanely annoying, every time i thought i was done there was more. But honestly, i learnt so much from this level, i have a better understanding of how to copy files, how the file command works, how files are understood in linux (i couldnt decompress the file unless i saved it in the format necessary). This was definitely the most difficult challenge yet, but also gave me the deepest insight into how Linux works.
## imagine i could write a script that did all of this for me?


## Update; finally completed level 13 all the way through to level 20
## Decided not to log progress after each level as i wanted to concentrate and maintain momentum
## The plan now is to move onto SadServers and then come back to bandit later
## then ill post the rest of my solutions for levels 13-20 in this progress file
## shoutout to CoderCo, this has been an amazing learning experience 
