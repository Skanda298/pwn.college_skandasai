# 1. cat — not the pet, but the command

This level required using the cat command to read the flag file that the challenge placed in my home directory.

## My Solve

**Flag:** 'pwn.college{8R2lVTggqwAANQuF8wV4a_ac4_c.QXxcTN0wSNwAzNzEzW}'

I read the flag file with cat:

```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{8R2lVTggqwAANQuF8wV4a_ac4_c.QXxcTN0wSNwAzNzEzW}
```
## What I learned

cat prints the contents of a file to standard output 

If invoked with no arguments, cat reads from standard input (useful for piping or manual input).

## References

The challenge description and the command output shown above.
One of the most critical Linux commands is cat. cat is most often used for reading out files, like so:

hacker@dojo:~$ cat /challenge/DESCRIPTION.md

One of the most critical Linux commands is `cat`.
`cat` is most often used for reading out files, like so:
cat will concatenate (hence the name) multiple files if provided multiple arguments. For example:
```
hacker@dojo:~$ cat myfile

This is my file!

hacker@dojo:~$ cat yourfile

This is your file!

hacker@dojo:~$ cat myfile yourfile

This is my file!

This is your file!
```
Finally, if you give no arguments at all, cat will read from the terminal input and output it. We'll explore that in later challenges...



# 2. Catting absolute paths

This level required using cat with an absolute path to read the flag file located at /flag.

## My Solve

**Flag:** 'pwn.college{8pAO5nvnmqWUbZh2hRcj19moSxt.QX5ETO0wSNwAzNzEzW}'

I read the flag by specifying the absolute path to the file:
```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{8pAO5nvnmqWUbZh2hRcj19moSxt.QX5ETO0wSNwAzNzEzW}
```
## What I learned

An absolute path begins with / and refers to the same location regardless of the current working directory.

cat /flag prints the contents of /flag directly 


## References

The challenge prompt explaining cat and the command output shown above.

You can specify cat's arguments as absolute paths:
```
hacker@dojo:~$ cat /challenge/DESCRIPTION.md

In the last level, you did `cat flag` to read the flag out of your home directory!

You can, of course, specify `cat`'s arguments as absolute paths:
```
In this directory, I will not copy it to your home directory, but I will make it readable. You can read it with cat at its absolute path: /flag.



# 3. More catting practice — absolute path without cd

This level required reading a flag that was placed in a different directory. The rules forbade using cd, so the flag had to be retrieved by specifying its absolute path to cat.

## My Solve

**Flag:** 'pwn.college{YmFBdTmpNAVJuy-CQIZ-j007zPr.QXwITO0wSNwAzNzEzW}'

I printed the flag directly with cat using the absolute path:
```
hacker@commands~more-catting-practice:~$ cat /usr/share/readline/flag

pwn.college{YmFBdTmpNAVJuy-CQIZ-j007zPr.QXwITO0wSNwAzNzEzW}
```
## What I learned

cat /usr/share/readline/flag reads the file regardless of the current working directory.

Absolute paths are reliable for accessing files placed elsewhere on the filesystem without changing directories.

## References

The challenge prompt stating the flag location and the command output shown above.
You can specify all sorts of paths as arguments to commands, and we'll practice some more with cat. In this level, I'll put the flag in some crazy directory, 
and I will not allow you to change directories with cd, so no cat flag for you. You must retrieve the flag by absolute path, wherever it is.



# 4. Grepping for a needle in a haystack

This level required using grep to search for the flag pattern inside a large text file.
 
## My Solve

**Flag:** 'pwn.college{oe5e9P2hCXutYF3NTQ5p6ntkQeB.QX3EDO0wSNwAzNzEzW}'

I searched the file for the pwn.college pattern and printed the matching line:
```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt

pwn.college{oe5e9P2hCXutYF3NTQ5p6ntkQeB.QX3EDO0wSNwAzNzEzW}
```
## What I learned

grep (pattern) (file) searches the file for lines matching the given pattern and prints matching lines.


## References

The command output shown above and standard grep usage.

Sometimes, the files that you might cat out are too big. Luckily, we have the grep command to search for the contents we need! We'll learn it in this challenge.

There are many ways to grep, and we'll learn one way here:
```
hacker@dojo:~$ grep SEARCH_STRING /path/to/file
```
Invoked like this, grep will search the file for lines of text containing SEARCH_STRING and print them to the console.
In this challenge, I've put a hundred thousand lines of text into the /challenge/data.txt file. grep it for the flag!

HINT: The flag always starts with the text pwn.college.


# 5. Comparing files 

this level requires you to find the difference between two files and get the flag

## My Solve

**Flag:** 'pwn.college{ksrleIxEWpG9mdPToO9DC3r4hyL.01MwMDOxwSNwAzNzEzW}'


I used diff to find the one line present in decoys_and_real.txt but not in decoys_only.txt.

```
diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt

19a20

> pwn.college{ksrleIxEWpG9mdPToO9DC3r4hyL.01MwMDOxwSNwAzNzEzW}
```
## What I learned

diff file1 file2 shows differences between two files.

The 19a20 means the extra line appears after line 16 of the first file and is line 17 in the second file.

For long files with many answers, diff is the fastest way to spot a single real flag.

# References
The two files used in the challenge and the exact diff output shown above.

When looking for changes between similar files, eyeballing them might not be the most efficient approach! This is where the diff command becomes invaluable.

diff compares two files line by line and shows you exactly what's different between them. For example:
```
hacker@dojo:~$ cat file1
hello
world
hacker@dojo:~$ cat file2
hello
universe
hacker@dojo:~$ diff file1 file2
2c2
< world
---
> universe
```
The output tells us that line 2 changed (2c2), with world in the first file (<) being replaced by universe in the second file (>).

Now for your challenge! There are two files in /challenge:

/challenge/decoys_only.txt contains 100 fake flags

/challenge/decoys_and_real.txt contains all 100 fake flags plus the one real flag



# 6. Listing Files

The challenge required me to use the ls command to inspect the contents of the /challenge directory. The output revealed a hidden executable file with a seemingly random name

## My Solve

**Flag:** 'pwn.college{E_YJa5sgiyCMbyzJB3ksolbiXVX.QX4IDO0wSNwAzNzEzW}'

```
hacker@commands~listing-files:~$ ls /challenge

23611-renamed-run-14298  DESCRIPTION.md
h
acker@commands~listing-files:~$ /challenge/23611-renamed-run-14298

Yahaha, you found me! Here is your flag:

pwn.college{E_YJa5sgiyCMbyzJB3ksolbiXVX.QX4IDO0wSNwAzNzEzW}
```
## What I learned

I learned how to use the ls command to list the contents of a directory. 
I also learned that you can execute a file by providing its full path on the command line

## References
The problem statement was the primary reference for this challenge.

So far, we've told you which files to interact with. But directories can have lots of files (and other directories) inside them, and we won't always be here to tell you their names. 
You'll need to learn to list their contents using the ls command!

ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided. Observe:
```
hacker@dojo:~$ ls /challenge
run
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ ls /home/hacker
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$
```
In this challenge, we've named /challenge/run with some random name! List the files in /challenge to find it.



# 7. Touching files

I created two files: /tmp/pwn and /tmp/college, and run /challenge/run to get the flag

## My Solve

**Flag:** 'pwn.college{8UZUy9PiZuDhEUukDUmyAL9_pKK.QXwMDO0wSNwAzNzEzW}'

I created two empty files in /tmp 
```
hacker@commands~touching-files:~$ touch /tmp/pwn

hacker@commands~touching-files:~$ touch /tmp/college

hacker@commands~touching-files:~$ /challenge/run

Success! Here is your flag:

pwn.college{8UZUy9PiZuDhEUukDUmyAL9_pKK.QXwMDO0wSNwAzNzEzW}
```
## What I learned

touch creates an empty file

After making the required files, run the challenge program (/challenge/run) to get the flag.

## References
The problem statement was the primary reference for this challenge.

Of course, you can also create files! There are several ways to do this, but we'll look at a simple command here. You can create a new, blank file by touching it with the touch command:
```
hacker@dojo:~$ cd /tmp

hacker@dojo:/tmp$ ls

hacker@dojo:/tmp$ touch pwnfile

hacker@dojo:/tmp$ ls

pwnfile

hacker@dojo:/tmp$

It's that simple! In this level, please create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get your flag!



# 8. Removing files

This challenge created a delete_me file in my home directory. I Deleted it, then ran /challenge/check which gave the flag

## My Solve

**Flag:** 'pwn.college{cwndxn9AlMHEMbfF3rc5fBKrvUT.QX2kDM1wSNwAzNzEzW}'

```
hacker@commands~removing-files:~$ rm delete_me 

hacker@commands~removing-files:~$ /challenge/check 

Excellent removal. 

Here is your reward: 

pwn.college{cwndxn9AlMHEMbfF3rc5fBKrvUT.QX2kDM1wSNwAzNzEzW}
```

## What I learned

rm  deletes a file from the filesystem 

You must be in the directory that contains the file

After removing the required file, run the provided checker to get the flag.

## References
The problem statement was the primary reference for this challenge.

Files are all around you. Like candy wrappers, there'll eventually be too many of them. In this level, we'll learn to clean up!

In Linux, you remove files with the rm command, as so:
```
hacker@dojo:~$ touch PWN

hacker@dojo:~$ touch COLLEGE

hacker@dojo:~$ ls

COLLEGE     PWN

hacker@dojo:~$ rm PWN

hacker@dojo:~$ ls

COLLEGE

hacker@dojo:~$

Let's practice. This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/check, which will make sure you've deleted it and then give you the flag!



# 9. Moving files

This challenge wants me to move the /flag file into /tmp/hack-the-planet

## My Solve

**Flag:** 'pwn.college{MQT-C2Pyh_LF_NW46FQU6vUmnXM.0VOxEzNxwSNwAzNzEzW}'

I moved the flag file:
```
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet

Correct! Performing 'mv /flag /tmp/hack-the-planet'.

hacker@commands~moving-files:~$ /challenge/check

Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:

pwn.college{MQT-C2Pyh_LF_NW46FQU6vUmnXM.0VOxEzNxwSNwAzNzEzW}
```
## What I learned

mv source destination moves files.

After performing the required file operation, run the challenge checker  to get the flag.

## References
The problem statement was the primary reference for this challenge.

You can also move files around with the mv command. The usage is simple:
```
hacker@dojo:~$ ls

my-file

hacker@dojo:~$ cat my-file

PWN!

hacker@dojo:~$ mv my-file your-file

hacker@dojo:~$ ls

your-file

hacker@dojo:~$ cat your-file

PWN!

hacker@dojo:~$
```
This challenge wants you to move the /flag file into /tmp/hack-the-planet (do it)! When you're done, run /challenge/check, which will check things out and give the flag to you.



# 10. Hidden files 

ls doesn't list all the files. So i had to go find a flag hidden as a dot-prepended file in /.

## My Solve

**Flag:** 'pwn.college{0dNajypLehZYK2YbALl0GJOi0nc.QXwUDO0wSNwAzNzEzW}'

I listed the root directory including hidden files, found a dotfile with the flag name, and then printed it.
```
hacker@commands~hidden-files:~$ ls -a / 

. .dockerenv bin challenge etc lib lib64 media nix proc run srv tmp var 

.. .flag-203872944011867 boot dev home lib32 libx32 mnt opt root sbin sys usr 

hacker@commands~hidden-files:~$ cat /.flag-203872944011867 

pwn.college{0dNajypLehZYK2YbALl0GJOi0nc.QXwUDO0wSNwAzNzEzW}
```
## What I learned

Files beginning with a . are hidden from a normal ls. 

Use ls -a  to see them.

ls -a / showed .flag-203872944011867 — that was the hidden flag file name.

cat /.flag-203872944011867 revealed the flag.

## References
The problem statement was the primary reference for this challenge.

Interestingly, ls doesn't list all the files by default. Linux has a convention where files that start with a . don't show up by default in ls and in a few other contexts.
To view them with ls, you need to invoke ls with the -a flag, as so:
```
hacker@dojo:~$ touch pwn

hacker@dojo:~$ touch .college

hacker@dojo:~$ ls

pwn

hacker@dojo:~$ ls -a

.college	pwn

hacker@dojo:~$
```
Now, it's your turn! Go find the flag, hidden as a dot-prepended file in /.



11. 

12. Making directories

I  created a /tmp/pwn directory and made a college file in it. Then ran /challenge/run which gave the flag

## My Solve

**Flag:** 'pwn.college{g85qgs9oVO3h5BJoLMwFZLCcDro.QXxMDO0wSNwAzNzEzW}'

I created a directory in /tmp, created the required file inside it, then ran the challenge:
```
hacker@commands~making-directories:~$ mkdir /tmp/pwn

hacker@commands~making-directories:~$ touch /tmp/pwn/college

hacker@commands~making-directories:~$ /challenge/run

Success! Here is your flag:

pwn.college{g85qgs9oVO3h5BJoLMwFZLCcDro.QXxMDO0wSNwAzNzEzW}
```
## What I learned

mkdir <dir> creates a new directory (here: /tmp/pwn).

After making the required filesystem changes, run the provided checker (/challenge/run) to get the flag.

## References
The problem statement was the primary reference for this challenge.

We can create files. How about directories? You make directories using the mkdir command. Then you can stick files in there!

Watch:
```
hacker@dojo:~$ cd /tmp

hacker@dojo:/tmp$ ls

hacker@dojo:/tmp$ ls

hacker@dojo:/tmp$ mkdir my_directory

hacker@dojo:/tmp$ ls

my_directory

hacker@dojo:/tmp$ cd my_directory

hacker@dojo:/tmp/my_directory$ touch my_file

hacker@dojo:/tmp/my_directory$ ls

my_file

hacker@dojo:/tmp/my_directory$ ls /tmp/my_directory/my_file

/tmp/my_directory/my_file

hacker@dojo:/tmp/my_directory$
```
Now, go forth and create a /tmp/pwn directory and make a college file in it! Then run /challenge/run, which will check your solution and give you the flag!



