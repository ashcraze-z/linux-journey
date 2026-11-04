# OverTheWire Bandit - Levels 0-5

Bandit 0-5 covers intro to SSH, basic file viewing, introduces new linux commands, hidden files and file navigation.

---

# Level 0 -> Level 1


In order to aquire the passward to Level 1 we have to login into bandit.labs.overthewire.org, on port 2220 using ssh. What is SSH?

SSH (secure shell) is a communication protocol designed for users to access and control remote computer over a netwrok. We are going to access the bandit server by using ssh.

The syntax for SSH is:
```
ssh [username]@[hostname or IP address] 
```
Let's understand this: What are the information we are given? We have the username (bandit0) and we also have **bandit.labs.overthewire.org** with port 2220

```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

we use `-p` to define specific port which we have to log in 

Now once we enter this it asks for password, OverTheWire have given us the password **bandit0**

Boom! We are now logged in bandit0 server 

<img width="902" height="930" alt="ichi" src="https://github.com/user-attachments/assets/b421bca5-9342-408a-ba41-7bf3972e89e6" />

--- 

## Basic Command

```bash
ls
```

`ls` is used to list all the files and directory in Linux

After using `ls` we get a file named readme , but how do we open it?

```bash
cat
```

`cat` command is commonly used for opening or viewing a file. 

```bash
cat readme
```

We get this 

 <img width="752" height="212" alt="ni" src="https://github.com/user-attachments/assets/752af02d-ca63-47e1-ba63-ece372aa5a11" />


We got the passowrd for next level **6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR**
 

---

# Level 1 -> Level 2

## Goal 

The password for next level is stores in a file called `-` which is located in home directory


---

## Command ❌

```bash
cat -
```

Why `cat -` won't work is `-` usually has another meaning in Linux.

## Command ✅

```bash
cat ./-
```

## Explanation of the command 

`cat` --> used to view or open a file

`.` --> this dot means current file

`/` --> this means search current directory

`./` --> search current directory 

`cat ./-` --> This means search in current directory for this file `-`

## Output

bandit1@bandit:~$ ls
-
bandit1@bandit:~$ cat ./-

PK8fYLZg2hnHSz83plBL1iEPKdD3QToB

bandit1@bandit:~$

Now we have the password for the next level Level 2


## Key Lesson 

There can be a different meaning to a command 

So we specify it to Linux by saying this is the filename 

```bash
./filename
```

---

# Level 2 -> Level 3

## Goal

The password for next level is stored in a file called `--spaces in this filename--`

The password for the next level is stored in a file named

```
--spaces in this filename--
```

There are spaces in this filename

---

## Command

```bash
cat ./--spaces\ in\ this\ filename--
```

## What is the problem

Linux seperates spaces with command and arugument

`cat` --> command
`file.txt` --> argument

When there is spaces in our argument `--spaces in this filename--` linux views this as multiple argument, when in reality it is one single file.


---


## Solution

We can use `\` backslash in our command 

```bash
cat ./--spaces\ in\ this\ filename--
```

`\` The backslash tells Linux that consider the `\` as part of the filename


## Key Lesson

we can use `\` to counter the spaces in a filename like

```
--spaces in this filename--
```

### Password for next Level, Level 4 is 

```
7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME
```

---


# Level 3 -> Level 4

## Goal

The password for the next level is stored in a **hidden file** in `inhere` directory

### Step 1 Do not forget inorder to view the listed files or directory present use ls

```
ls
```

--- 

## New Command

```
cd
```

---

## Explanation 

`cd` command which is shortform of **Change Directory** is used when you have to go to directory. 

### How do you know which is a directory and which is not?

Here

<img width="252" height="42" alt="san" src="https://github.com/user-attachments/assets/557af749-b7fc-4542-9f70-81ad0af4b7f8" />

<img width="187" height="42" alt="yon" src="https://github.com/user-attachments/assets/8983b716-75c5-4c7b-b836-420a6ed56ea0" />

You can notice the difference, the directory is highlighted in blue 

## Command

```bash
cd inhere
```

We change the directory and go to `inhere` which was listed as directory in `ls`


<img width="256" height="107" alt="go" src="https://github.com/user-attachments/assets/e85e41c7-e802-42a1-ab76-70e0155169be" />

---

## Why ls did not work 

but to our surprise when we use `ls` command we cannot see the list of files present in that directory `inhere`

### New Command

```bash
ls -la
```

`ls -la` is a command in Linux which is used to list all files and directories in the current directory in detailed format including **hidden files**

It provides Additional Information 

```text
owner
permissions
group
size
data
hidden file
```

YES using `ls -la` we can view the hidden files which was the goal of this level 


<img width="592" height="105" alt="roku" src="https://github.com/user-attachments/assets/bfae0304-0fc1-49f7-9727-1cee02836514" />

<img width="432" height="37" alt="nana" src="https://github.com/user-attachments/assets/81fa619e-4d32-45a0-9288-fc681f726462" />


After getting the hidden file, we do 

```bash
cat ...Hiding-From-You
```

Then we get the password for next level


---

## Key Lesson

Linux treats filename starting with `.` as hidden file 

```bash
ls
```

Does not show

```bash
ls -la
```

shows.

### Password for Level 5

**xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq**


---


# Level 4 -> Level 5

## Goal

The password for next Level is stored in the only only-human readable file in the `inhere` directory.


---

use `ls` to list the directory

```bash
cd inhere
```

go inside the directory `inhere`

## List the files inside the inhere directory

```bash
ls
```

```
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
```

---

## Command 

```
cat ./*
```

we use `*` to open all the existing files inside the current directory using `./`

we combine them to get

```
./*
```

After this you will get a bunch a random characters with the human readable password, which we want.

```
bandit4@bandit:~/inhere$ cat ./*
���f�Gy���}��nS��2����[a����f� ݡkK����Vʁ�3)��h�,����c����;�
�J�ç�����␦t1ht����@���9
                       f�;��t��X�
p���i~���C��Eh�3�6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG7�k�?g*�g�H|�7�#n�4�`�,���ĳ�PC��I7
fU�^��ʩq,�W�M���M�ÿ@ЬD^V�H�<qQ[Q�΄���6:�
```

We only take the password and move on to next level


---

## Key Lesson 

`*` is used to open all the file in the existing directory

`cat ./*` 

### Password for Level 5 

**6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG7**


---

# Level 4 -> Level 5






 


