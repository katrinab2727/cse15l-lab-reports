# Lab 1 Report

## `cd` Command

**No Arguments**
```
[user@sahara ~/lecture1]$ cd
[user@sahara ~]$
```
The working directory was lecture1 when `cd` was run. Using `cd` without an argument sets the working directory to home, so the current directory was changed from lecture1 to home.

**Path to a Directory as an Argument**
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$
```
The working directory was home before the command was run. When a path to a directory is used as an argument for `cd`, the working directory is changed to the directory directed in the path. In this case, the path was only to lecture1, so the current directory was changed to lecture1.

**Path to a File as an Argument**
```
[user@sahara ~]$ cd lecture1/messages/en-us.txt
bash: cd: lecture1/messages/en-us.txt: Not a directory
```
With home being the working directory at the time of the command, an error message was outputted because `cd` can only take in arguments that are directories, so the path must lead to a directory. Since the path lead to a file, an error occured because the working directory can not be changed to a file.

## `ls` Command

**No Arguments**
```
[user@sahara ~]$ ls
lecture1
```
Becuase the current directory was home when `ls` was used with no arguments, it listed the files in the home directory, showing lecture1.

**Path to a Directory as an Argument**
```
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
```
Even though the working directory was home, `ls` listed the files in the lecture1 directory because lecture1 was used as an arugment.

**Path to a File as an Argument**
```
[user@sahara ~]$ ls lecture1/messages/en-us.txt
lecture1/messages/en-us.txt
```








