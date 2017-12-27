# Linux-basics

*A repo containing general linux commands*


### Directory and File Management ###

`mkdir -p z/y/x`  -  to make a directory inside a directory

`rm -r z/y/x`  -  remove a directory

`cp -r src proj`  -  copy a folder to other folder
 
`more myfirstfile_copy.txt`  - to view a large file don't use cat use more to display in a paginated way

`tail myfirstfile_copy.txt`  -  defaults to last 10 lines

`tail -20 myfirstfile_copy.txt`  - last 20 lines

`head -20 myfirstfile_copy.txt`

### Finding ###

`find . -name '*.txt'`  -  to find in the current directory with the name matching the pattern 

`grep myword file1 file2`  -  locate myword in files

`grep -r myword directory`  -  to locate in directory

`grep -i myword file1 file2`   -  for case insensitive searches

### Word/Line Count ###

`wc`  -  wordcount in a file, lines+words+characters

`wc -l`  -  line count in a file 

### Permissions ###

`ls -la myfile`  -  to view the details of a file

`ls -la`  -  for all the files in the current directory

`chmod u+x myfile`  -  to give permission to user to execute 

`chmod u-x myfile`  -  to remove permission to user to execute

`chmod u+rw,g+rw myfile`  -  similarly g for group, no space before after comma

`chmod o-w,g-w myemptyfile`  -  removes write permissions from others and groups 


*The output of ls -la is of format permissions for user, for group, for others in pairs of rwx*

### Process Management ###

`ps aux`  -  to see all of the processe by all of the users

`ps`  -  it only lists users processes

`top`  -  to continuously monitor processes

### Foreground/Background Jobs ###

*To run a command in the background, put a & in the end of the command*
eg 
`ls &` or `sleep 60 &`

`kill processid`  -  to kill a process 

`jobs`  -  to see the list of all running jobs, job id is different from process id

`fg jobid`  or  `fg %jobid`  -  to bring a job to the foreground

`bg`  -  To bring a running command to the background first close it with `ctrl + z` and than use `bg`

`screen`  -  To keep a process running in the background even if the shell has been disconnected, similarly use `nohup`

eg. of using nohup, in order to run jupyter notebook despite the closing of the shell use 
`nohup jupyter-notebook`

`pstree`  -  to see the tree of processes

`kill -9 1`  -  shutsdown the system

### Scripting in Bash ###

*A example script*

```
#!/bin/bash
name=linux
echo "hello $name world"

``` 

save it as script.sh, than run `chmod +x script.sh`

You can than run the script by running `./script.sh`

####  In Unix, the extension doesn't dictate the program to be used while executing a script. It is the first line of the script that would dictate which program to use. In the example above, the program is "/bin/bash" which is a Unix shell. 
#### `#!` is called shebang. If your file starts with `#!/path/to/something`, the standard is to run something program first and pass the rest of the file to that program as an input.
#### eg. `#!/usr/bin/python` (Script will be run by python interpreter)

`echo $?`  -  to check the exit status/ return value of the previous command, it gives 0 if the previous command was run successfully and non zero number corresponding to the error if there is error.

*There are some programs that need to keep running all the time. Such programs are called services.
You can communicate with such programs even from another computer. These programs or processes bind themselves to a port. No two programs can listen on same port.* 


You can connect and talk to any service using nc command in the following way:

`nc computer_name(or ip_address) port_number`

If you want to give multiple names to a single file without copying the content, you can create the link. Much like a alias for the file. This creates a hardlink i.e once you delete the original file the link remains intact .Use

`ln orig_text mylink`

To create a symbolic link. A symbolic link points to a file. In case, the original file is deleted, the symbolic link would be pointing to non-existing file. Use

`ln -s orig_text1 myslink`

*We cannot create hardlink to a directory*

Say, you want to execute a command only if another command is successful then you use &&.
And if you want a command to be executed if another command has failed, you use ||.
 

 eg. `(ls -l tea_ready && echo "Tea is ready") || echo "Tea is not ready"`


### Redirecting the output ###

`echo "hello" > hello.out`  -  to put the output of the echo in hello.out

`echo "world" >> hello.out`  -  to append the output of echo to the file

*If we want to send the output of one program to another, we can use pipe. A pipe is denoted by "|".*

eg. `echo "Hello, World" | wc`

Script for wordcount

```
tr 'A-Z' 'a-z'| sed -E 's/[ \t]+/\n/g'|sed 's/[^0-9a-z]//g' | sort|uniq -c|sort -nr -S 50M
``` 

To run it using a file with the help of pipe do - 
`cat /cxldata/big.txt | ./wordcountscript.sh | more`



In Unix, there is a file /etc/shadow that contains (one-way)encrypted passwords of every user. The user can not see the contents of the file. This is to defend the password cracking programs.

To change the password, user needs to use the command: passwd. This passwd command first asks you for your old password and encrypts your input and compares it against the value in the file /etc/shadow. If it matches then it updates the password file /etc/shadow with new content.

When you are not allowed to view the /etc/shadow file, how can a program (passwd) do the same when run by you?

This is where the idea of a special permission called setuid come into picture. A program file can be given setuid permission such that program becomes the user who owns the program file instead of the user who is running it.

You can make a program setuid by giving 's' instead of 'x' permission. If you have written a script x.sh, an example would be:

`chmod +s x.sh`

`sudo commandname`  -  to run the command as a superuser

`sudo visudo`  -  to modify the sudoers

`shutdown -h now`  -  to shutdown the system

`reboot`  -  to reboot the system

`which java`  -  tells where the program java is located

### Unix shell provides environment variables. To see the entire list of environment variables, use: ###

`set`

for example - $PS1 variable is used by the shell to display the prompt. To change your prompt:

`PS1='xxx>>'`

To find the value of a environment variable use - 

`echo $environmentvariable`

To set a environment variable simply do myvar=value, where myvar is our environment variable. 

eg. 
```
MYV=myfile
ls $MYV
``` 
























