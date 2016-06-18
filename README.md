# MyShell

Simple unix shell written in C that reads user commands into a buffer, then parses and executes those commands with forked processes.

Supports file redirection and background processes:

* `&` execute command in the background
* `>` redirect standard output of a command to a file
* `>>` redirect & append standard output of a command to a file
* `2>` redirect standard error of a command to a file
* `2>>` redirect & append standard error of a command to a file
* `<` redirect standard input of a command to come from a file

To compile and run:

```
$ gcc -o myshell myshell.c -std=c99 -pthread
$ ./myshell
```

To exit, enter `exit` when using the shell.

### Example usage

Note: the maximum number of tokens that can be entered is 7.

```
MyShell> /bin/echo 1 2 3 > file.txt &
MyShell> cat file.txt
1 2 3
```
```
MyShell> ls -l >> file.txt
MyShell> cat file.txt
1 2 3
total 19
-rwxrwxrwx 1 root root    91 Dec 12  2015 error.c
-rwxrwxrwx 1 root root     6 Jun 18 10:20 file.txt
-rwxrwxrwx 1 root root 11748 Jun 18 10:14 myshell
-rwxrwxrwx 1 root root  5328 Dec 21 08:18 myshell.c
-rwxrwxrwx 1 root root     9 Jun 18 09:58 README.md
```
```
MyShell> gcc -o error error.c
MyShell> ./error 2> file.txt 
MyShell> cat file.txt
derp!
```
```
MyShell> ./error 2>> file.txt
MyShell> cat file.txt
derp!
derp!
```
```
MyShell> grep party < /usr/share/dict/words > file.txt
MyShell> cat file.txt
party
party's
partying
```
```
MyShell> exit
$ 
```
