# 1. The Root
This challenge prompted me to invoke a program by providing its path on the command line.
The path was '/pwn'.

## My solve
**flag:** 'pwn.college{YKuVqKDPG3z45W8pc5p8w2cuGfX.QX4cTO0wSNwAzNzEzW}'

In the problem statement, it was provided that if i prove the path for the program '/pwn', it would providw the flag.
'''

hacker@paths~the-root:~$ /pwn

BOOM!!!

Here is your flag:

pwn.college{YKuVqKDPG3z45W8pc5p8w2cuGfX.QX4cTO0wSNwAzNzEzW}

## What i learned
I learned to invokoe the path for a program  
I learned to invove '/pwn'

## References
The problem statement was the reference used
so the filesystem starts at /. Under that, there are a whole mess of other directories, configuration files, programs, and, most importantly, flags. 
In this level, we've added a program right in /, called pwn, that will give you the flag. All you need to do for this level is to invoke this program!

You can invoke a program by providing its path on the command line. In this case, you'll be giving the exact path, starting from /, so the path would be /pwn. 
This style of path, one that starts with the root directory, is referred to as an "absolute path".
'''


# 2. Program and Absolute Paths

this challenge requires you to invoke a program by providing its absolute path.
the absolute path was '/challege/run'.

## My solve
**flag:** 'pwn.college{Mzt1CQA1uEYWp_13JhvRWFYpVrb.QX1QTN0wSNwAzNzEzW}'

In the problem statement, it was provided that xecute the run file that is in the challenge directory that is, in turn, in the / directory, it will give the flag
'''

hacker@paths~program-and-absolute-paths:~$ /challenge/run

Correct!!!

/challenge/run is an absolute path! Here is your flag:

pwn.college{Mzt1CQA1uEYWp_13JhvRWFYpVrb.QX1QTN0wSNwAzNzEzW}

## What I learned
I learned to invoke the absolute path of a program
I learned to invoke '/challenge/run'

## References
The problem statement was the reference
the challenge directory and the challenge directory is, in turn, right in the root directory (/). The path to the challenge directory is, thus, /challenge. 
The name of the challenge program in this level is run, and it lives in the /challenge directory. Thus, the path to the run challenge program is /challenge/run.

This challenge again requires you to execute it by invoking its absolute path.
 You'll want to execute the run file that is in the challenge directory that is, in turn, in the / directory.
 If you invoke the challenge correctly, it will give you the flag.


# 3. Position thy Self

The challenge required changing the shell's current working directory using cd, then executing the challenge program /challenge/run from that directory.

## My Solve
**Flag:** ' pwn.college{MFcDZNweRANIOVCNgWfb3vOrKa2.QX2QTN0wSNwAzNzEzW}'

I followed the instructions to change into /var/log and then ran the challenge binary from there:
'''


hacker@paths~position-thy-self:~$ /challenge/run

Incorrect...

You are not currently in the /var/log directory.

Please use the `cd` utility to change directory appropriately.

hacker@paths~position-thy-self:~$ cd /var/log

hacker@paths~position-thy-self:/var/log$ /challenge/run

Correct!!!

/challenge/run is an absolute path, invoked from the right directory!

Here is your flag:

pwn.college{MFcDZNweRANIOVCNgWfb3vOrKa2.QX2QTN0wSNwAzNzEzW}

## What I learned
The shell maintains a current working directory; many programs may check it before completing their task.
cd /var/log changes the shell's current directory to /var/log.
Executing a program by absolute path (e.g. /challenge/run) still checks the current working directory of the shell that invoked it.

## References
The problem statement and the challenge program output shown above.
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$

This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out.
This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program.


# 4. Position elsewhere

The challenge required changing the shell's current working directory using cd to /usr/share/build-essential, then executing the challenge program /challenge/run from that directory.

## My Solve
**Flag:** 'pwn.college{waRMoTLHBl-ImdvpKMY4DWxle1Q.QX3QTN0wSNwAzNzEzW}'

I changed into the required directory and ran the challenge binary
'''

hacker@paths~position-elsewhere:~$ cd /usr/share/build-essential

hacker@paths~position-elsewhere:/usr/share/build-essential$ /challenge/run

Correct!!!

/challenge/run is an absolute path, invoked from the right directory!

Here is your flag:

pwn.college{waRMoTLHBl-ImdvpKMY4DWxle1Q.QX3QTN0wSNwAzNzEzW}

hacker@paths~position-elsewhere:/usr/share/build-essential$

## What I learned
You must place your shell in the correct current working directory before running some challenge programs.
cd /usr/share/build-essential sets the shell’s working directory to /usr/share/build-essential.

## References
The challenge prompt and the /challenge/run program output shown above.

The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$

This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. 
This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program.


# 5. Position yet elsewhere

The challenge required changing the shell's current working directory using cd to /tmp, then executing the challenge program /challenge/run from that directory.

## My Solve
**Flag:** ' pwn.college{o7wry_RTLjSFzoWDwhOUFW5Z_YE.QX4QTN0wSNwAzNzEzW}'

I changed into the required directory and ran the challenge binary:
'''

hacker@paths~position-yet-elsewhere:~$ cd /tmp

hacker@paths~position-yet-elsewhere:/tmp$ /challenge/run

Correct!!!

/challenge/run is an absolute path, invoked from the right directory!

Here is your flag:

pwn.college{o7wry_RTLjSFzoWDwhOUFW5Z_YE.QX4QTN0wSNwAzNzEzW}

## What I learned
The shell’s current working directory matters — some programs check it before proceeding.
Use cd /tmp to set the working directory to /tmp.

## References
The challenge prompt and the /challenge/run program output shown above.

The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

hacker@dojo:~$ cd /some/new/directory

hacker@dojo:/some/new/directory$

This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out.
This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program.


6. Implicit relative paths from /

This level demonstrated relative paths: you must invoke the challenge program using a relative path while your current working directory is /.

## My Solve
**Flag:**  'pwn.college{sZai0AOqO0Z3gYymbFoPF04EvPh.QX5QTN0wSNwAzNzEzW}'

I changed to the root directory / and ran the program using a relative path (no leading /):
'''

hacker@paths~implicit-relative-paths-from-:~$ cd /

hacker@paths~implicit-relative-paths-from-:/$ challenge/run

Correct!!!

challenge/run is a relative path, invoked from the right directory!

Here is your flag:

pwn.college{sZai0AOqO0Z3gYymbFoPF04EvPh.QX5QTN0wSNwAzNzEzW}

hacker@paths~implicit-relative-paths-from-:/$

## What I learned
A relative path does not start with / and is interpreted relative to the current working directory (cwd).
When cwd is /, a relative path challenge/run refers to /challenge/run.
Because the level required a relative invocation, I ran challenge/run (not /challenge/run) from /.

## References
The challenge instructions explaining relative vs absolute paths and the program output shown above.

If you put in absolute paths everywhere, then it really doesn't matter what directory you are in, as you likely found out in the previous three challenges.
However, the current working directory does matter for relative paths.

A relative path is any path that does not start at root (i.e., it does not start with /).
A relative path is interpreted relative to your current working directory (cwd).
Your cwd is the directory that your prompt is currently located at.
This means how you specify a particular file, depends on where the terminal prompt is located.

Imagine we want to access some file located at /tmp/a/b/my_file.

If my cwd is /, then a relative path to the file is tmp/a/b/my_file.
If my cwd is /tmp, then a relative path to the file is a/b/my_file.
If my cwd is /tmp/a/b/c, then a relative path to the file is ../my_file. The .. refers to the parent directory.



# 7. Explicit relative paths from /

This level required invoking the challenge program using an explicit relative path (one that uses ./) while the current working directory is /.

## My Solve
**Flag:** 'pwn.college{UZ1xN68F9PGAlcrFifytXe6LBXR.QXwUTN0wSNwAzNzEzW}'

I changed to the root directory / and ran the program with an explicit relative path:
'''

hacker@paths~explicit-relative-paths-from-:~$ cd /

hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run

Correct!!!

./challenge/run is a relative path, invoked from the right directory!

Here is your flag:

pwn.college{UZ1xN68F9PGAlcrFifytXe6LBXR.QXwUTN0wSNwAzNzEzW}


## What I learned
./ refers to the current directory; ./challenge/run therefore resolves to /challenge/run when the cwd is /.
Explicit relative paths (starting with ./) and "naked" relative paths (no ./) can refer to the same file depending on cwd.
Knowing the difference between absolute (/challenge/run), implicit relative (challenge/run), and explicit relative (./challenge/run) paths is important for how a program is located by the shell.

## References
In most operating systems, including Linux, every directory has two implicit entries that you can reference in paths: . and ... The first, ., refers right to the same directory,
so the following absolute paths are all identical to each other:

/challenge

/challenge/.

/challenge/./././././././././

/./././challenge/././

The following relative paths are also all identical to each other:

challenge

./challenge

./././challenge

challenge/.

Of course, if your current working directory is /, the above relative paths are equivalent to the above absolute paths.The challenge instructions explaining . and .. and the program output shown above.



# 8. Implicit relative path

This level required running the run program from inside the /challenge directory using an explicit relative invocation (./run) because a "naked" name (run) is not searched for in the current directory by default.

## My Solve
**Flag:** 'pwn.college{8sG6kJUx1HS-b5Y4Dl_D4sBClRo.QXxUTN0wSNwAzNzEzW}'

I changed into /challenge and executed the program using a relative path that explicitly refers to the current directory:
'''

hacker@paths~implicit-relative-path:/$ cd /challenge

hacker@paths~implicit-relative-path:/challenge$ ./run

correct!

./run is a relative path, invoked from the right directory!

Here is your flag:

pwn.college{8sG6kJUx1HS-b5Y4Dl_D4sBClRo.QXxUTN0wSNwAzNzEzW}

## What I learned
The shell does not search the current directory for executables when you type a "naked" command name (e.g., run). This is a safety measure.
To run a program that resides in the current directory, you must specify a relative path such as ./run.
. refers to the current directory; ./run tells the shell explicitly “run the run program located right here.”

## References
The challenge instructions explaining . and why the current directory isn't searched implicitly, and the /challenge/run program output shown above.
This challenge will need you to run it from the /challenge directory. Here, things get slightly tricky.

Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path. Consider the following:

hacker@dojo:~$ cd /challenge

hacker@dojo:/challenge$ run

This will not invoke /challenge/run. This is actually a safety measure: if Linux searched the current directory for programs every time you entered a naked path, 
you could accidentally execute programs in your current directory that happened to have the same names as core system utilities! As a result, the above commands will yield the following error:

bash: run: command not found

learn how to explicitly use relative paths to launch run in this scenario.
The way to do this is to tell Linux that you explicitly want to execute a program in the current directory, using . like in the previous levels



# 9. Home Sweet Home
The challenge required providing a path to /challenge/run that was absolute, inside my home directory, and three characters or less.

## My Solve
**Flag:** 'pwn.college{QGsGZoFkOOylS2vS-vyINtSVmeX.QXzMDO0wSNwAzNzEzW}'

Bash

hacker@paths~home-sweet-home:~$ /challenge/run ~/a

Writing the file to /home/hacker/a!

... and reading it back to you:

pwn.college{QGsGZoFkOOylS2vS-vyINtSVmeX.QXzMDO0wSNwAzNzEzW}

## What I learned
 learned that the ~ shorthand is expanded by Bash into an absolute path to the home directory before a command is executed.
 I also learned that you must specify a filename, not just a directory, when writing to a location. The final solution combined these two pieces of knowledge to successfully meet all the challenge's constraints.


## References
The problem statement and the error messages from the program itself were my guides.

Every user has a home directory, typically under /home in the filesystem. In the dojo, you are the hacker user, and your home directory is /home/hacker.
The home directory is typically where users store most of their personal files. As you make your way through pwn.college, this is where you'll store most of your solutions.

Typically, your shell session will start with your home directory as your current working directory. Consider the initial prompt:

hacker@dojo:~$

The ~ in this prompt is the current working directory, with ~ being shorthand for /home/hacker.
 Bash provides and uses this shorthand because, again, most of your time will be spent in your home directory. 
Thus, whenever bash sees ~ provided as the start of an argument in a way consistent with a path, it will expand it to your home directory. Consider:

hacker@dojo:~$ echo LOOK: ~

LOOK: /home/hacker

hacker@dojo:~$ cd /

hacker@dojo:/$ cd ~

hacker@dojo:~$ cd ~/asdf

hacker@dojo:~/asdf$ cd ~/asdf

hacker@dojo:~/asdf$ cd ~

hacker@dojo:~$ cd /home/hacker/asdf

hacker@dojo:~/asdf$

Note that the expansion of ~ is an absolute path, and only the leading ~ is expanded. This means, for example, that ~/~ will be expanded to /home/hacker/~ rather than /home/hacker/home/hacker.


hacker@dojo:~$ cd /tmp

hacker@dojo:/tmp$ cd

hacker@dojo:~$

Now it's your turn to play! In this challenge, /challenge/run will write a copy of the flag to any file you specify as an argument on the commandline, with these constraints:

Your argument must be an absolute path.
The path must be inside your home directory.
Before expansion, your argument must be three characters or less.
Again, you must specify your path as an argument to /challenge/run as so:

hacker@dojo:~$ /challenge/run YOUR_PATH_HERE





