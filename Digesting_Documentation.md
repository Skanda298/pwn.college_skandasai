# 1. Learning from documentation 

The program for this challenge was /challenge/challenge, I invoked it to get the flag

## My Solve

**Flag:** 'pwn.college{8zPQjWKNaSCLep2VB3krwwSWPhE.QX0ITO0wSNwAzNzEzW}'

I ran the challenge program with the --giveflag argument
```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag

Correct argument! Here is your flag:

pwn.college{8zPQjWKNaSCLep2VB3krwwSWPhE.QX0ITO0wSNwAzNzEzW}
```
## What I learned

I learned that --giveflag is an argument you add when running the program. 

It tells the program to give the flag.

## References
The problem statement was the major reference

The typical need you'll have for documentation is just to figure out how to use all these dang programs, and a specific case of that is figuring out what arguments to specify on the command line.
This module will mostly dig into that concept, as a proxy for figuring out how to use the programs in general. Through the rest of the module,
you'll go through various ways of asking the environment for help for the programs, but first, we'll dig into the concept of reading documentation.

The correct usage of programs depends, in a large part, on the proper specification of arguments to them.
Recall the -a of ls -a in the hidden files challenge of the Basic Commands module: that -a was an argument that told ls to list out hidden files as well as non-hidden files.
Because we wanted to list out hidden files, invoking ls with the -a argument was the correct way to use it in our scenario.

The program for this challenge is /challenge/challenge, and you'll need to invoke it properly in order for it to give you the flag. Let's pretend that this is its documentation:

Welcome to the documentation for /challenge/challenge! To properly run this program, you will need to pass it the argument of --giveflag. Good luck!



# 2. Learning complex usage

I ran the challenge program with an argument that told it to print a file: /challenge/challenge --printfile /flag.

## My Solve

**flag:** 'pwn.college{kt_k5htMkiyecw8N9dTgw-vbthA.QX1ITO0wSNwAzNzEzW}'

I ran the program with --printfile /flag:
```
/challenge/challenge --printfile /flag

Correct argument! Here is the /flag file:

pwn.college{kt_k5htMkiyecw8N9dTgw-vbthA.QX1ITO0wSNwAzNzEzW}
```

## What I learned

--printfile /flag tells the program to print the contents of the file /flag.
Arguments can include filenames so the program knows which file to show.

## References

The problem statement was the major reference
While using most commands is straightforward, the usage of some commands can get quite complex. For example, the arguments to commands like sed and awk, 
which we're definitely not getting into right now, are entire programs in an esoteric programming language! 
Somewhere on the spectrum between cd and awk are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the find level in Basic Commands. find has a -name argument, 
and the -name argument itself takes an argument specifying the name to search for. Many other commands are analogous.

Here is this level's documentation for /challenge/challenge:

Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal, when given the --printfile argument. The argument to the --printfile argument is the path of the flag to read. For example, /challenge/challenge --printfile /challenge/DESCRIPTION.md will print out the description of the level!

Given that documentation, go get the flag!



# 3. Reading manuals 

I read the program's manual with man challenge to find the correct argument, then ran the program with that argument.

## My Solve

**Flag:** 'pwn.college{E66DI_c3a6MYoc2BXXPnZwtiU5L.QX0EDO0wSNwAzNzEzW}'

I ran:
```
hacker@man~reading-manuals:~$ man challenge
 
CHALLENGE(1)                                                                  Challenge Commands                                                                  CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --caocnw NUM
              print the flag if NUM is 663

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                                        May 2024                                                                       CHALLENGE(1)
 Manual page challenge(1) line 1/31 (END) (press h for help or q to quit) q 

hacker@man~reading-manuals:~$ /challenge/challenge --caocnw 663
Correct usage! Your flag: pwn.college{E66DI_c3a6MYoc2BXXPnZwtiU5L.QX0EDO0wSNwAzNzEzW}
```

## What I learned

man challenge shows the manual page and documents --caocnw NUM.
Passing --caocnw 663 tells the program to print the flag.

## References
This level introduces the man command. man is short for manual, and will display (if available) the manual of the command you pass as an argument. For example, let's say we wanted to learn about the yes command (yes, this is a real command):
```
hacker@dojo:~$ man yes
This will display the manual page for yes, which will look something like this:

YES(1)                           User Commands                          YES(1)

NAME
       yes - output a string repeatedly until killed

SYNOPSIS
       yes [STRING]...
       yes OPTION

DESCRIPTION
       Repeatedly output a line with all specified STRING(s), or 'y'.

       --help display this help and exit

       --version
              output version information and exit

AUTHOR
       Written by David MacKenzie.

REPORTING BUGS
       GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
       Report any translation bugs to <https://translationproject.org/team/>

COPYRIGHT
       Copyright  ©  2020  Free Software Foundation, Inc.  License GPLv3+: GNU
       GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
       This is free software: you are free  to  change  and  redistribute  it.
       There is NO WARRANTY, to the extent permitted by law.

SEE ALSO
       Full documentation <https://www.gnu.org/software/coreutils/yes>
       or available locally via: info '(coreutils) yes invocation'

GNU coreutils 8.32               February 2022                          YES(1)
```
Manpages are stored in a centralized database. If you're curious, this database lives in the /usr/share/man directory, but you never need to interact with it directly:
you just query it using the man command. The arguments to the man command aren't file paths, but just the names of the entries themselves (e.g., 
you run man yes to look up the yes manpage, rather than man /usr/bin/yes, which would be the actual path to the yes program but would result in man displaying garbage).

The challenge in this level has a secret option that, when you use it, will cause the challenge to print the flag. You must learn this option through the man page for challenge!

# 4. Searching Manuals

I opened the program's manual with man challenge, searched the page for the right option, then ran /challenge/challenge with that option to get the flag.

## My Solve

**Flag:** 'pwn.college{EZJmeI_CvXh3R6vB5ZXETc78yTs.QX1EDO0wSNwAzNzEzW}'

I ran:
```
man challenge
# searched the man page for the option, then:
 /challenge/challenge <option-found-in-man>
```

and the program printed the flag.

## What I learned

man opens a program's manual so I can read its options.

Use / inside man to search for text and n to go to the next match.

## References

The problem statement was the major reference

You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards!

Find the option that will give you the flag by reading the challenge man page.


# 5.  Searching for Manuals
I used the man -k challenge command to find a hidden executable named asncqfkrcq. I then read its manual page using man asncqfkrcq to figure out the correct usage to get the flag.

## My Solve

**Flag:** 'pwn.college{IasncqK0fDPSkWrMVc29OT970Wq.QX2EDO0wSNwAzNzEzW}'

I wrote:
```
hacker@man~searching-for-manuals:~$ man man

hacker@man~searching-for-manuals:~$ man -k challenge

asncqfkrcq (1) - print the flag!

hacker@man~searching-for-manuals:~$ man asncqfkrcq

hacker@man~searching-for-manuals:~$ /challenge/challenge --asncqf 029

Correct usage! Your flag: pwn.college{IasncqK0fDPSkWrMVc29OT970Wq.QX2EDO0wSNwAzNzEzW}
```
## What I learned

man is the command to read the manual page for other commands.

man -k is used to search for keywords across all the available command manual pages.

## References
The problem statement was the major reference.

This level is tricky: it hides the manpage for the challenge by randomizing its name. 
Luckily, all of the manpages are gathered in a searchable database, 
so you'll be able to search the man page database to find the hidden challenge man page! To figure out how to search for the right manpage, 
read the man page manpage by doing: man man!

HINT 1: man man teaches you advanced usage of the man command itself, and you must use this knowledge to figure out how to search for the hidden manpage that will tell you how to use /challenge/challenge

HINT 2: though the manpage is randomly named, you still actually use /challenge/challenge to get the flag!


6. Helpful Programs

I ran the program with --help to find the -p option, which revealed the secret value of 423 needed to get the flag with -g 423.

## My Solve
Flag: pwn.college{UdZmnbV4EeUp2aq-NnKvJpDrKaO.QX3IDO0wSNwAzNzEzW}

I ran;
```
hacker@man~helpful-programs:~$ /challenge/challenge --help

usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

<...truncated help output...>

hacker@man~helpful-programs:~$ /challenge/challenge -p --print-value

The secret value is: 423

hacker@man~helpful-programs:~$ /challenge/challenge -g 423

Correct usage! Your flag: pwn.college{UdZmnbV4EeUp2aq-NnKvJpDrKaO.QX3IDO0wSNwAzNzEzW}
```
## What I learned
The --help or -h option is used to show the usage and available options of functions
This is the fastest way to figure out how a new command works without having to look up the full manual page.

## References
The problem statement was the major reference.

Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. Usually, this argument is --help, but it can often be -h or, in rare cases,
-?, help, or other esoteric values like /? (though that latter is more frequently encountered on Windows).

In this level, you will practice reading a program's documentation with --help. Try it out!

Given that knowledge, go get the flag!


7.  Help for Builtins

I used the help challenge command to find the required --secret value, which was oZzufqTL, and executed the command with this value to get the flag.

## My Solve

Flag: pwn.college{oZzufqTL9LM6ki7KPc8pf84swcw.QX0ETO0wSNwAzNzEzW}

I ran:

hacker@man~help-for-builtins:~$ help challenge

challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune           display a fortune
      --version           display the version
      --secret VALUE      prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "oZzufqTL".

hacker@man~help-for-builtins:~$ challenge --secret oZzufqTL

Correct! Here is your flag!

pwn.college{oZzufqTL9LM6ki7KPc8pf84swcw.QX0ETO0wSNwAzNzEzW}

## What I learned

You can get a list of shell builtins by running the builtin help

You can get help on a specific one by passing it to the help builtin

## References

The problem statement was the major reference.
Some commands, rather than being programs with man pages and help options, are built into the shell itself. These are called builtins. 
Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. 
You can get a list of shell builtins by running the builtin help, as so:
```
hacker@dojo:~$ help
You can get help on a specific one by passing it to the help builtin. Let's look at a builtin that we've already used earlier, cd!

hacker@dojo:~$ help cd
cd: cd [-L|[-P [-e]] [-@]] [dir]
    Change the shell working directory.
    
    Change the current directory to DIR.  The default DIR is the value of the
    HOME shell variable.
```
Some good information! In this challenge, we'll practice using help to look up help for builtins. 
This challenge's challenge command is a shell builtin, rather than a program. 
Like before, you need to lookup its help to figure out the secret value to pass to it!
