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

`wc`  -  wordcount in a file

`wc -l`  -  line count in a file 

### Permissions ###

`ls -la myfile`  -  to view the details of a file

`ls -la`  -  for all the files in the current directory

`chmod u+x myfile`  -  to give permission to user to execute 

`chmod u+x myfile`  -  to remove permission to user to execute

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

``




