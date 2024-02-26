# Lab 4 Report

## Vim

### Step 1 - Log into ieng6

<img width="682" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/15c9b8eb-c49a-4744-9460-1bc5de137c0d">

Keys Pressed: `<up><enter>`

**Command run: `ssh kbosler@ieng6.ucsd.edu`**

I had this command in my command history. It was the most recent command I typed in my local computer's terminal, so only one `<up>` was needed. The command logs me onto the CSE server using ssh for the ieng6 machine.

### Step 2 - Clone fork of the repository

<img width="500" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/2c0e9810-44e0-49a0-b391-133c023487a8">

Keys Pressed: `git clone git@github.com:katrinab2727/lab7.git`

**Command run: `git clone git@github.com:katrinab2727/lab7.git`**

I did not have this command in my command history, so I had to type it all out. This command clones the directory from Github to my current server on the ieng6 machine.

### Step 3 - Run the tests, demonstrating that they fail

<img width="594" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/72089b58-4c3b-4ade-ab2f-d9187107f601">

Keys Pressed: `cd l<tab><enter>bash test.sh<enter>`

**Commands run: `cd lab7/` and `bash test.sh`**

The first command changes the working directoy to the `lab7/` directory. By using `<tab>` after only typing `l`, the only directory starting with `l` was brought up as a shortcut. I then ran the tests by using the `test.sh` script that runs the test library and test file.

### Step 4 - Edit the code file to fix the failing test

<img width="596" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/e07b3895-e5f1-4939-8db7-512e17f9ca8b">

Keys Pressed: `vim L<tab>.j<tab><enter>44Gexi2<esc>:wq<enter>`

**Command run: `vim ListExamples.java`**

The command runs `vim` on the java file to edit it from the terminal. 

`44G`: brings the cursor to line 44, which is where the edit needs to be made. 

`e`: brings the cursor to the end of `index1`

`x`: deletes the `1`

`i2`: enters insert mode and adds 2

`<esc>`: changes back to normal mode

`:wq`: saves the changes and quits `vim`

### Step 5 - Run the tests, demonstrating that they now succeed

<img width="338" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/a24abf71-141c-4e35-8147-5389effaa5b9">

Keys Pressed: `<up><up><enter>`

**Command run: bash test.sh**

I was able to run the tests again by using the command from my command history. They now passed due to the edit that fixed code.


### Step 6 - Commit and push the resulting change to my Github account

<img width="608" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/881f01dc-87e0-4060-8f7e-d566d9647a1c">

Keys Pressed: `git add L<tab>.j<tab><enter>git commit -m "lab 4 report - vim :D" && git push origin main`

**Command run: `git add ListExamples.java` and `git commit -m "lab 4 report - vim :D" && git push origin main`**

The first command added the changes to the file to get rid of the bug and I used the previously mentioned shortcut to help run this command by using `<tab>`. I did not have the second command in my history, so I had to type it all. The command commits the changes made locally to github along with the message "lab 4 report - vim :D". It then pushes the commited changes to the main branch of the remote repository named origin.

