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

> By default most command line programs send their output to the standard
output which by default displays it on the
```sh
commandName >fileName -Overwrites the file with the output of
the command
commandName >>fileName - appends the file with the output of
the command.
```
> Most of the command line programs accept its input from the standard
input and by default gets its contents from the keyboard. Similar to
standard output it can also be redirected.
sort < filename - sort command processes the contents of the file with the
name filename.
sort < file1 > file2 processes the contents of file 1 and redirects its
output to file 2

