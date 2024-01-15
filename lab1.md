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
The working directory was home when the command was run. When a path to a directory is used as an argument for `cd`, the working directory is changed to the directory directed in the path. In this case, the path was only to lecture1, so the current directory was changed to lecture1.

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
Becuase the current directory was home when `ls` was used with no arguments, it listed the files and directories in the home directory, showing lecture1.

**Path to a Directory as an Argument**
```
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
```
Even though the working directory was home, `ls` listed the files and directories in the lecture1 directory because lecture1 was used as an arugment.

**Path to a File as an Argument**
```
[user@sahara ~]$ ls lecture1/messages/en-us.txt
lecture1/messages/en-us.txt
```
When `ls` was used with a path to a file as an argument, the path used as an argument was the output. The command is used to print out the files for a directory, so the path to the file was printed as a replacement. The working directory when the command was used was once again home.

## `cat` Command

**No Arguments**
```
[user@sahara ~]$ cat


```
By using `cat` without any argurments in the home directory, the command reads from the terminal because it has no files to read. The command prints back what is types in the terminal, so when I pressed enter to create a new line, the command printed another line as well.

**Path to a Directory as an Argument**
```
[user@sahara ~]$ cat lecture1
cat: lecture1: Is a directory
```
Using the command on a directory causes as error because `cat` is used to concatenate files together, which can not be done with a directory. The current directory was home when the command was run.

**Path to a File as an Argument**
```
[user@sahara ~]$ cat lecture1/messages/en-us.txt
Hello World!
```
The working directory was home, so a path to a file was used as an argument. `cat` then outputted what was in the en-us.txt file. Since only one file was used, the file was concatenatted to nothing and printed its contents into the terminal.







