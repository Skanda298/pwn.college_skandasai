# 1. Matching with *

I used the * globbing character to find and change into the target directory. The command cd /ch* expanded to cd /challenge, successfully moving my working directory to /challenge, where I then executed the program to retrieve the flag.

## My Solve

**Flag:** 'pwn.college{4ePnFNYIk0hFXxj4ParFH4ooM4U.QXxIDO0wSNwAzNzEzW}'

I ran:
```
hacker@globbing~matching-with-:~$ cd /ch*

hacker@globbing~matching-with-:/challenge$ /challenge/run

You ran me with the working directory of /challenge! Here is your flag:

pwn.college{4ePnFNYIk0hFXxj4ParFH4ooM4U.QXxIDO0wSNwAzNzEzW}
```
## What I learned

When it encounters a * character in any argument, the shell will treat it as a "wildcard" and try to replace that argument with any files that match the pattern.

## References

The problem statement was the major reference

The first glob we'll learn is *. When it encounters a * character in any argument, the shell will treat it as a "wildcard" and try to replace that argument with any files that match the pattern.
It's easier to show you than explain:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_*
Look: file_a file_b file_c
```
Of course, though in this case, the glob resulted in multiple arguments, it can just as simply match only one. For example:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: file_*
Look: file_a
```
When zero files are matched, by default, the shell leaves the glob unchanged:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: nope_*
Look: nope_*
```
The * matches any part of the filename except for / or a leading . character. For example:
```
hacker@dojo:~$ echo ONE: /ho*/*ck*
ONE: /home/hacker
hacker@dojo:~$ echo TWO: /*/hacker
TWO: /home/hacker
hacker@dojo:~$ echo THREE: ../*
THREE: ../hacker
```
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use globbing to keep the argument you pass to cd to at most four characters! 
Once you're there, run /challenge/run for the flag!



# 2. Matching with ?

I used the ? globbing character to find and change into the /challenge directory. The command cd /?ha??enge successfully matched the path by using ? to replace the single unknown characters in the path, 
allowing me to run the program from the correct working directory and retrieve the flag.

## My Solve

**Flag:** 'pwn.college{4kmXxAl1542Blr1sRTgdwPQc86g.QXyIDO0wSNwAzNzEzW}'

I ran:
```
hacker@globbing~matching-with-:~$ cd /?ha??enge

hacker@globbing~matching-with-:/challenge$ /challenge/run

You ran me with the working directory of /challenge! Here is your flag:

pwn.college{4kmXxAl1542Blr1sRTgdwPQc86g.QXyIDO0wSNwAzNzEzW}
```
## What I learned

When it encounters a ? character in any argument, the shell will treat it as a single-character wildcard. 

## References

The problem statement was the major reference.

Next, let's learn about ?. When it encounters a ? character in any argument, the shell will treat it as a single-character wildcard. This works like *, but only matches one character. For example:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_cc
hacker@dojo:~$ ls
file_a	file_b	file_cc
hacker@dojo:~$ echo Look: file_?
Look: file_a file_b
hacker@dojo:~$ echo Look: file_??
Look: file_cc
```
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use the ? character instead of c and l in the argument to cd! Once you're there, run /challenge/run for the flag!


# 3. Globbing Character Ranges
I used a character range glob file_[abhs] to match the individual files that contained the characters a, b, h, and s 
This was passed as one argument to /challenge/run, which gave  the flag.

## My Solve
**Flag:** 'pwn.college{EaDYoKNbEy0mszErLxplQfGEI2h.QXzIDO0wSNwAzNzEzW}'

I ran:
```
hacker@globbing~matching-with-:~$ cd /challenge/files

hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[abhs]

You got it! Here is your flag!

pwn.college{EaDYoKNbEy0mszErLxplQfGEI2h.QXzIDO0wSNwAzNzEzW}
```
## What I learned

The square brackets [] are a globbing pattern used by the shell to match any  character from the set inside them.

## References
The problem statement was the major reference.

Next, we will cover []. The square brackets are, essentially, a limited form of ?, in that instead of matching any character, [] is a wildcard for some subset of potential characters, 
specified within the brackets. For example, [pwn] will match the character p, w, or n. For example:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
```
Try it here! We've placed a bunch of files in /challenge/files. Change your working directory to /challenge/files and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h!


# 4. Matching Paths with []

I used the character range glob [] as part of an absolute path to solve the challenge. The pattern /challenge/files/file_[bash]

## My Solve

**Flag:** 'pwn.college{IrzZ6r0aTrlXtF83MK8vuh6tuTb.QX0IDO0wSNwAzNzEzW}'

I ran:
```
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]

You got it! Here is your flag!

pwn.college{IrzZ6r0aTrlXtF83MK8vuh6tuTb.QX0IDO0wSNwAzNzEzW}
```
## What I learned

[] globbing pattern works on path segments, not just filenames, meaning you can use it anywhere in an unquoted path.

## References

The problem statement was the major reference.

Globbing happens on a path basis, so you can expand entire paths with your globbed arguments. For example:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: /home/hacker/file_[ab]
Look: /home/hacker/file_a /home/hacker/file_b
```
Now it's your turn. Once more, we've placed a bunch of files in /challenge/files. Starting from your home directory, 
run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files!


# 5. Matching Words Containing a Character

I used the  *p* to match any filename in the directory that contained the letter 'p', which gave the flag

## My Solve

**Flag:** 'pwn.college{8j4wk4a0FpKKjY21yXy2FrbfH-I.0lM3kjNxwSNwAzNzEzW}'

I ran:
```
hacker@globbing~matching-paths-with-:~$ cd /challenge/files

hacker@globbing~matching-paths-with-:/challenge/files$ /challenge/run *p*

You got it! Here is your flag!

pwn.college{8j4wk4a0FpKKjY21yXy2FrbfH-I.0lM3kjNxwSNwAzNzEzW}
```
## What I learned

*p* can be used to narrow down all the possible filenames that contain the letter p 

## References

The problem statement was the major reference.

So far, you've specified one glob at a time, but you can do more! Bash supports the expansion of multiple globs in a single word. For example:
```
hacker@dojo:~$ cat /*fl*
pwn.college{YEAH}
hacker@dojo:~$
```
What happens above is that the shell looks for all files in / that start with anything (including nothing), then have an f and an l, and end in anything (including ag, which makes flag).

Now you try it. We put a few happy, but diversely-named files in /challenge/files. Go cd there and run /challenge/run, providing a single argument:
a short (3 characters or less) globbed word with two * globs in it that covers every word that contains the letter p.


# 6. Mixing Globs

I successfully used  combined glob pattern [cep]* to match the files "challenging," "educational," and "pwning," which satisfied the challenge. 

## My Solve

**Flag:** 'pwn.college{8bb0hdmGvIOa8uclFz6V9TWGrdD.QX1IDO0wSNwAzNzEzW}'

I ran:
```
hacker@globbing~mixing-globs:~$ cd /challenge/files

hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*

You got it! Here is your flag!

pwn.college{8bb0hdmGvIOa8uclFz6V9TWGrdD.QX1IDO0wSNwAzNzEzW}
```

## What I learned

The square brackets [] globbing pattern can be combined with the * wildcard to create powerful, yet concise, matching patterns.

This technique is highly effective for matching a short, specific set of files that share common letters but have widely differing lengths.

## References

The problem statement was the major reference.

Now, let's put the previous levels together! We put a few happy, but diversely-named files in /challenge/files. Go cd there and, using the globbing you've learned, 
write a single, short (6 characters or less) glob that (when passed as an argument to /challenge/run) will match the files "challenging", "educational", and "pwning"!


# 7. Exclusionary Globbing

I successfully used the  glob [^pwn]* to match all files within the /challenge/files directory that did not begin with the letters 'p', 'w', or 'n', satisfying the challenge. 

## My Solve

**Flag:** 'pwn.college{IR2hubYIeMfjUijI6oQXTGlMKxZ.QX2IDO0wSNwAzNzEzW}'

I ran:
```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files

hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*

You got it! Here is your flag!

pwn.college{IR2hubYIeMfjUijI6oQXTGlMKxZ.QX2IDO0wSNwAzNzEzW}
```

## What I learned

f the first character in the brackets is a ! or ^, the glob inverts,
and that bracket instance matches characters that aren't listed.

References
The problem statement was the major reference.

Sometimes, you want to filter out files in a glob! Luckily, [] helps you do just this. If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts,
and that bracket instance matches characters that aren't listed. For example:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[!ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[^ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
```
Armed with this knowledge, go forth to /challenge/files and run /challenge/run with all files that don't start with p, w, or n!

NOTE: The ! character has a different special meaning in bash when it's not the first character of a [] glob, so keep that in mind if things stop making sense! ^ does not have this problem,
but is also not compatible with older shells.



# 8. Tab Completion

I used the tab completion feature of the shell by typing cat /challenge/pwn<TAB>, which  completed the necessary filename and showed the flag.

## My Solve

**Flag:** 'pwn.college{cfwshWMBdIZ4To37fMbYB8mLBF9.0FN0EzNxwSNwAzNzEzW}'

I ran:
```
hacker@globbing~tab-completion:~$ ls /challenge

DESCRIPTION.md  pwncollege​

hacker@globbing~tab-completion:~$ cat /challenge/pwn<TAB>

pwn.college{cfwshWMBdIZ4To37fMbYB8mLBF9.0FN0EzNxwSNwAzNzEzW}
```
## What I learned

Tab completion is a feature  that automatically completes file paths when you press the <TAB> key.

## References
The problem statement was the major reference.
As tempting as it might be, using * to shorten what must be typed on the commandline can lead to mistakes. 
Your glob might expand to unintended files, and you might not spot it until the rm command is already running! No one is safe from this style of error.

A safer alternative when you are trying to specify a specific target is tab completion. If you hit tab in the shell, it'll try to figure out what you're going to type and automatically complete it.
Auto-completion is super useful, and this challenge will explore its use in specifying files.

This challenge has copied the flag into /challenge/pwncollege, and you can freely cat that file. But you can't type the filename: we used some serious trickery to make sure that you must tab-complete it. Try it out!
```
hacker@dojo:~$ ls /challenge
DESCRIPTION.md  pwncollege
hacker@dojo:~$ cat /challenge/pwncollege
cat: /challenge/pwncollege: No such file or directory
hacker@dojo:~$ cat /challenge/pwn<TAB>
pwn.college{HECK YEAH}
hacker@dojo:~$
```
When you hit that tab key, the name will expand and you'll be able to read the file. Good luck!



# 9. Multiple Options for Tab Completion

I used tab completion to navigate the ambiguous file list and find the name of the flag file.
After identifying the file pwncollege-flag among the multiple options, I used the cat to get the flag.

## My Solve

**Flag:** 'pwn.college{coc4R-80Akow7JcQvXLdsLWOMHz.0lN0EzNxwSNwAzNzEzW}'

I ran:
```

hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ /challenge/files/pwn

pwn                    pwn-the-planet         pwncollege-flamingo    pwncollege-hacking

pwn-college            pwncollege-family      pwncollege-flyswatter

hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ /challenge/files/pwn-college

hack-the-planet        pwn-the-planet         pwncollege-flamingo

pwn                    pwncollege-family      pwncollege-flyswatter

pwn-college            pwncollege-flag        pwncollege-hacking

hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat pwncollege-flag

pwn.college{coc4R-80Akow7JcQvXLdsLWOMHz.0lN0EzNxwSNwAzNzEzW}
```

## What I learned

When tab completion results in multiple files, you can press <TAB> again to view the options and narrow down the choice.

## References
The problem statement was the major reference.
Consider the following situation:
```
hacker@dojo:~$ ls
flag  flamingo  flowers
hacker@dojo:~$ cat f<TAB>
```
There are multiple options! What happens?

What happens varies based on the specific shell and its options. By default bash will auto-expand until the first point when there are multiple options (in this case, fl).
When you hit tab a second time, it'll print out those options. Other shells and configurations, instead, will cycle through the options.

This challenge has a /challenge/files directory with a bunch of files starting with pwncollege. Tab-complete from /challenge/files/p or so, and make your way to the flag!



# 10. Tab Completion on Commands

The challenge required executing a command that started with pwncollege to retrieve the flag. 
I used tab completion by typing t pwncollege and pressing the <TAB> key to auto-complete the correct command, and then used cat to get the flag.

## My Solve

**Flag:** 'pwn.college{coOSvKlPwJwd0XDzdE86boagI7Y.0VN0EzNxwSNwAzNzEzW}'

I ran:
```
hacker@globbing~tab-completion-on-commands:~$ pwncollege-32228 cat pwncollege-32228

Correct! Here is your flag:

pwn.college{coOSvKlPwJwd0XDzdE86boagI7Y.0VN0EzNxwSNwAzNzEzW}

```
## What I learned

Tab completion works on command names, not just file path by completing the command after you press the <TAB> key.


## References
The problem statement was the major reference.
Tab completion is for more than files! You can also tab-complete commands. This level has a command that starts with pwncollege, and it'll give you the flag. Type pwncollege and hit the tab key to auto-complete it!

NOTE: You can auto-complete any command, but be careful: callous auto-completes without double-checking the result can wreak havoc in your shell if you accidentally run the wrong commands!
