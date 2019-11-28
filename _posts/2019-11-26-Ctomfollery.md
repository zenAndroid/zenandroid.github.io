---
layout: post
title: Some C tomfoolery
tags: quick-notes
---

# Hey

Real quick post, just to get used to regularly updating this blog.

# fopen("mkdir/mkdir.txt","rw") #

So while i was using C for a systems programming assignement, I had to create a a file in a './temp/file.txt'.

Obviously I then go on to use fptr = fopen("./temp/entier.txt","w");

Except that it turns out it doesn't work, this was surprising to me, until i thaught a bit about it and remembered that since this is C we're dealing with, it probably can't create inexsisting directories in fopen calls.

So i use this to make sure the directory exists before making the fopen call.

```c
    if (stat("./temp", &st) == -1) {
        mkdir("./temp",0700);
    }
```

stat is to test whether the directory exists, if it doesn't, then ... mkdir !

# system("...") statements are ugly, but sometimes ... #

So basically in this assignement, i had to get a process to perform ac action and then notify another process after a certain event.

And the method of notifications is sending signals.

The problematic part is that the only information you know about this other second process, is its name.

And given that the kill function ``kill(pid_t pid, int SIGNUM)`` needs a NUMBER/PID and not a string/name, i had to grab the pid of this program at runtime.

The perfectionist I am, i try to make the damn thing as foolproof as it can be (ie as portable as i can)

But the fact that there was no C function to do this (figure out the PID of a program given only its name), i had to resort to system-specific things.

You see, bash (and i assume, linux as an ecosphere in general) has quite a number of useful command that can kinda serve this purpose, commands such as:
* pgrep
* pidof
* pkill
* etc

But i dont like using such system-specific things.

In the end however, I ended up using them as i thought this specific situation doesnt call for premature micro-optimizations and frankly, i didn't care enough.

The way i did it was ``cmd = popen("pidof affiche","r");``, this opens up a FILE\*-handle that i can read the result of the execution from.

<b>What do you mean you think I tried to implement a /proc crawler to analyse the cmdline file in every entry of the OS's list of running processes ? I DID NO SUCH THING !!!!</b>

Then i just cast it to an unsigned long (I wonder if there's a reason its long, not integer, given that PID number probably wont be very high, oh well)

Now, i supposedly have the PID, so i just kill the process with SIGUSR1;

And of course, on the other side, I installed a custom signal-handler, that does things.


# TLDR ? #

Honeslty I'm not much proud of this, I mean i did try some error-handling, but, EH, not much.
I did not do this assignement as a programmer, but more as a script kiddie, not much i can be proud of really ..

Still, i intend to mess more with this stuff later ...


Adios.


