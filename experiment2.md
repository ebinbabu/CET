##### Experiment No:2

##   Linux commands for operations such as redirection, pipes,filters,job control,changing ownership | permissions of files/links/directory.


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
```
>  ### 2.6 Permissions

 Permissions

| Command | Operation |
| -------- | --------- |
| chmod | modify file access rights |
| su | become super user |
| chown | change file ownership |
| chgrp | change file group ownership |

>  ### 2.7 Links
A link provides a connection between files. This provides the ability to have a
single file or directory referred to through different names.
The nearest comparison with the Windows world is of a shortcut, but that
is an unfair comparison as a link in Linux is far more powerful. A Windows
shortcut is just a way of launching a file from a different place, whereas a link
can make a file appear in multiple locations which is invisible to the applications.
There are two types of links that can be created. The first is a hard link
and the other is a soft link (sometimes called symbolic link or symlink). The
command to create these is the same - ln.
- Hard Link A hard link creates a second file that refers to the same file
on the physical disk. This is achieved by having two filenames that point
directly at the same file. This is normally used where file entries (links)
are on the same filesystem. When a hard link is created then all the
names that link to that file are given the same status. Deleting one of
the files will break the link, but the file can still exist under the other
linked filenames. This works by maintaining a counter of the number of
filenames that the file has. When the number of filenames reaches zero
then the file is considered to be deleted and is removed.
The number of filenames for a file can be seen using the ‘ls -l’ command.
The number following the file permissions indicates the number of linked
filenames. The following screenshot shows that filename1 and filename2
are to linked files with one of the file denoted by the 2 (in this case the  same file, but they could be to completely different files), the file not link is a single file denoted by the 1.
```sh
$ls -l
```
> total 2432
-rw-r--r-- 2 stewart stewart 1241088 2009-01-23 15:26 filename1
-rw-r--r-- 2 stewart stewart 1241088 2009-01-23 15:26 filename2
-rw-r--r-- 1 stewart stewart 0 2009-01-23 15:26 not\_link 

Note that whilst the two files appear to occupy 1.2Mb each the actual space used is only 1.2Mb in total as the file only exists once.
```sh
$du -h
```
 1.2M
 
The default for the ln command is a hard link. Assuming filename1 already exists filename2 is created using:
```sh
$ln filename1 filename2
```
 - Soft Link
A soft link is sometimes referred to as a symbolic link or symlink. A
filename created as a soft link is a special file that has the pathname of
the file to redirect to. Behind the scenes when you try and access a symlink
it just goes to the filename referred to instead.
In the following example a file has been created called original file with
a soft link to that same file called softlink tofile. As you can see the ls
command makes it clear that this is a link through the l at the beginning
of the file permissions and due to the reference notation after the filename.

```sh
$ls -l
```
 > total 440
-rw-r--r-- 1 stewart stewart 446464 2009-01-23 15:21 original_file
lrwxrwxrwx 1 stewart stewart 13 2009-01-23 15:20 softlink_tofile -> original_file 

Note that with a soft link the permissions to the link file are set to full access as the user is contstrained by the permissions on the original file. Also note that if the filesize of the original file changes the link will remain the same (on this system 13 bytes).
If the link is deleted then this will have no impact on the original file, but if the original file is deleted this will result in a broken link. The example below shows how removing the original file results in a error "No such file or directory".
```sh
$ rm original_file
$ ls -l
```
  total 0
lrwxrwxrwx 1 stewart stewart 13 2009-01-23 15:20 softlink_tofile -> original_file  
```sh
$ cat softlink_tofile
```
cat: softlink_tofile: No such file or directory
The -s option is used on the ln command to create a softlink.
ln -s original_file softlink_tofile
Note that if original file does not exist then the soft link will be
created anyway. An attempt to read it will give the error message we
encountered earlier, but an attempt to write to the file can create origi-
nal file.

- Pitfalls while using links
  - There are some things that you need to be aware of, particularly
when using softlinks.
  - Some programs (e.g. Apache) can be configured to not follow soft
links (from a security
  - When creating backup files you need to be aware of how the particular
backup program / tool  
  - Using one method the program may not backup the file referenced
resulting in an incomplete backup of the
  - Using another method the program may end up backing up both as
individual files using double the space for that
  - Using the second method of the above could result in the file being
restored as a real file rather than as a link, breaking their connection
  -  The original file could be deleted without realising that there are
other symlinked files referring to it
Despite these pitfalls there are many advantages to using both hard
and soft links to provide multiple references to files.
>  ### 2.8 Output

>  ### 2.9 Result
The linux commads for redirection of standard I/O, pipes, filters, job control
and links in linux were studied and they were run on ArchLinux 4.10.11 and
output was verified.

