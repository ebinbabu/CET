##### Experiment No:1

##   Getting started with Linux basic commands for directory operations


>  ### 1.1   Aim
#####  Getting started with Linux basic commands for directory operations, displaying directory structure in tree format etc. 
### 1.2 Basic Commands 

| Command | Operation |
| ------ | ------ |
|  $ touch filename | create a new file |
| $ mkdir filename | create a new directory |
| $pwd | prints present working directory |
| $cd dirname  | change directory |
| $cat filename  | view contents of a file |
| $more filename  | view contents of a file one scornful at a time |
   | $less filename | similar but faster than more |
   | $ls   | list files in a directory |
   |$ ls -l or ll| provide long listing of all the files |
   | $ls -l -h    | provides sizes in human readable form |
   | $ls   -F   | mark all executables with * and directories with / |
   |$ls -a | show all files in the present directory |
   |$cp file1 file2 | copying files |
   |$cp -r dir1 dir2 | copy directories |
   | $rm filename | remove a file |
   | $rm -r directory name| remove directory |
   |$ clear | clear the contents of the terminal |
   |$locate | find files by name |
   |$man  |commandname view help of the specified command name |
   |$chmod [who what which] filename |  change file permissions |
   |$chown username:groupname filename |  change ownership file or directory |
   | $kill [options] pid | Kill a process|
   |$who [options]  | Display who is logged in |
   |$top  | Display the resources being used in your system  |
   |$ln [options] source desitination | Create a shortcut |
    
  ### 1.3 Directory Structure in Linux


  ![N|Solid](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcSm8jdFwD46XIqbrfiNbuAboIcuNjrz3L_bDs-w-kpRayrC56rI)
  
   ![N|Solid](https://github.com/ebinbabu/CET/blob/master/filesystem.png.png?raw=true)
  ### 1.4  Output

![Lab1](https://github.com/ebinbabu/CET/blob/master/lab1.png?raw=true)
![N|Solid](https://github.com/ebinbabu/CET/blob/master/lab2.png?raw=true)
![N|Solid](https://github.com/ebinbabu/CET/blob/master/lab3.png?raw=true)
![lab4](https://raw.githubusercontent.com/ebinbabu/CET/master/lab4.png)




  ### 1.6 Result
#####  Several basic linux commands and the direcotry structure of linux were studied

















##### Experiment No:2

##   Linux commands for operations such as redirection, pipes,filters,job control


>  ### 2.1   Aim
Linux commands for operations such as redirection, pipes, filters, job control

>  ### 2.2 Redirection of standard Input/Output

- By default most command line programs send their output to the standard
output which by default displays it on the
```sh
commandName >fileName -Overwrites the file with the output of the command
commandName >>fileName - appends the file with the output of the command.
```
- Most of the command line programs accept its input from the standard
input and by default gets its contents from the keyboard. Similar to
standard output it can also be redirected.
```sh
sort < filename - sort command processes the contents of the file with the name filename.
sort < file1 > file2 processes the contents of file 1 and redirects its output to file 2
````
>  ### 2.3 Pipes
- Pipes are used to redirect the standard output of one command to the standard
input of another command.
```sh 
command1 | command2 the standard output of command 1 is redirected to the standard input of command 2.
```
>  ### 2.4 Filters
Filters take the standard input and perform an operation upon it and sends
the results to the standard output. This can be used to process information in
powerful ways.
- sort - sorts the standard input and sends the output to standard output.
‘sort filename’ rearranges each line of file in alphabetical order and
outputs it to the standard output.
- uniq - Given a sorted stream of data from standard input it removes the
duplicate lines of data and returns the result to the standard output.
- grep - examines each line of data it receives from standard input and
outputs all lines that contains a specific pattern of characters.
```sh
‘$ grep “string” new.txt’ outputs lines of text in new.txt which contain the word string.
```
- fmt - reads text from standard input and outputs formatted text to stan-
dard output.
```sh
$ fmt filename’ formats contents of filename and outputs it in standard output.
```
- pr - Takes data from the standard input and splits the data into pages
with page breaks, footers and headers in preparation for printing.
```sh 
$ pr filename’ displays the contents of the file one page after the other and returns the output to the standard output
```
- head - Outputs the first few lines of the file and returns it to the standard
output.
```sh
$ head /etc/passwd
```
-  tail - Outputs the last few lines of the file and returns it to the standard
output.
```sh
$ tail /etc/passwd
```

- tr - Translates Characters. Can be used to perform tasks such as uppercase
to lowercase conversions or changing the line termination characters from
one type to another.
```sh
tr [:lower:] [:upper:]’ takes input from the keyboard and outputs each character of the input to uppercase characters and outputs it to the standard output
```
>  ### 2.5 Job Control
There are several commands used to control processes in Linux.
-  ps - The ps commands lists the processes running in the system.
```sh 
$ ps all processes running in the system
$ ps aux’ lists all processes running in the system
```
- kill - sends a signal to the specified processes usually to stop the execution
of the processes. ‘kill -l’ lists the signal names that can be sent to
processes in Linux.
```sh 
$ kill PID to kill the processes specified by the process id (pid) which can be obtained by the ps command
$ kill -s SIGKILL pid’ is used to send SIGKILL signal to process with process id ‘pid’. This command is used to forcefully kill a process without memory cleanup A signal is an asynchronous notification sent to a process or to a specific thread within the same process in order to notify it of an event that occurred7
```
- jobs - An alternate way of listing the processes. jobs is a shell builtin command which gives you information internal to the shell such as the job numbers
```sh 
$ jobs lists the jobs that the current shell is managing.
$ bg - used to put a process in background.
$ fg - used to put a process in foreground
