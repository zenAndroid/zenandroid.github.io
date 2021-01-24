---
layout: post
title: Quick notes
tags: xargs ffmpeg opus quick-notes leet-hacc
description: Very quick post to brag about a one liner, but also to attempt and explain it.
---

Look, it's a small blog post, it's a bite sized blog post, it's a ...

# Quick post #

## mp3, opus, and ffmpeg ##

Let me remind you, dear reader, or future-me, that i am not very ~~knowledgable~~^H^H^H^H^H^H^H^H^H^H^H^H ~~discerning~~ strict about my music formats.

I was looking at my music directory and i was kinda of bothered at the size of it all, not that it matters all that much, since i largely have enough space for plenty of music (not that music takes much space to be honest), but still i had a couple minutes to burn and, remembering i have `ffmeg`, the task seemed easy to do.
So the input files are in mp3, and looking around and **remembering that youtube-dl's --best-audio option always led to opus (and remarking from previous downloads that it was a lot more compact**, i thought I'd convert things into opus music files.

(By the way, most people seem to agree that the opus file format is pretty compact and high quality even though it's lossless, so /shrug.

### FFMPEG usage ###
Using ffmpeg is pretty simple, as long as your use case is trivially ... Trivial
```bash
ffmpeg -i input.mp3 output.opus
```
And it turns out my use case is exactly that, which surprised me as i had the misguided assumption that it'd be more difficult than that (i thought you had to be an expert in codecs and encoding formats and algorithms before using the tool and such), oh the silly assumptions we make.

So, it's a done deal right, i just use the tool for the files i have and that's it right?

Well, if i want to go to each mp3 file and apply this manually, sure.

But I'm not that inefficient right?

~~Technically even if i was i wouldn't post about it, beware survivorship bias ...~~

Would be great if i can :

1- List all the files
2- Execute the above command for each

### Drop the charade ###

This was never about the space savings, it was all about curiosity, I'm sorry I lied.

Well, first of all let's build up the blocks slowly.

To list the files in a directory, it's pretty straightforward, we just have to make sure each file output is on a separate line, and that is easy using the `ls --format=single-column` or the equivalent `ls -1`.

OK, so now we have the first part solved, not particularly impressive.

Now we have a list of folders(of mp3 files), we need to actually convert them using the command showed earlier.

Something like...

```scheme
(map (lambda(x) (sh-command "ffmpeg -i " x " outPutFilename")) (sh-command "ls -1"))
```
The command that helps you achieve this is the one and only:

```bash
ls -1 \*mp3 | xargs -I{} -n 1 -P 0 ffmpeg -i{} {}.opus
```

NAME

xargs - build and execute command lines from standard input

SYNOPSIS

xargs [options] [command [initial-arguments]]

**-I replace-str**

Replace occurrences of replace-str in the initial-arguments with names read from standard input.  Also,  unquoted  blanks  do  not terminate input items; instead the separator is the newline character.  Implies -x and -L 1.

**-n max-args, --max-args=max-args**

Use at most max-args arguments per command line.  Fewer than max-args arguments will be used if the size (see the  -s  option)  is exceeded, unless the -x option is given, in which case xargs will exit.

**-P max-procs, --max-procs=max-procs**

Run  up  to max-procs processes at a time; the default is 1.  If max-procs is 0, xargs will run as many processes as possible at a time.  Use the -n option or the -L option with -P; otherwise chances are that only one exec will be done.  While xargs is running, you  can  send its process a SIGUSR1 signal to increase the number of commands to run simultaneously, or a SIGUSR2 to decrease the number.  You cannot increase it above an implementation-defined limit (which is shown with --show-limits).  You cannot decrease it below  1.  xargs never terminates its commands; when asked to decrease, it merely waits for more than one existing command to ter‐ minate before starting another.

Please note that it is up to the called processes to properly manage parallel access to shared resources.  For  example,  if  more than one of them tries to print to stdout, the output will be produced in an indeterminate order (and very likely mixed up) unless the processes collaborate in some way to prevent this.  Using some kind of locking scheme is one way to prevent such problems.  In general, using a locking scheme will help ensure correct output but reduce performance.  If you don't want to tolerate the perfor‐ mance difference, simply arrange for each process to produce a separate output file (or otherwise use separate resources).

## Recap ##

I used, other than the `-i` flag (input), three more flags, to which I've showed the manual's description.
The -P flag basically enables multi-processing, and so executes multiples processes for the given stdin.
The -n flag means something that i found unintuitive.
Basically, say you have this file filled with lines, and this tool that can build and execute commands from stdin. You'd think that the default would be that it executes the command given to it to each line right?
Well that's also what i thought, but it is not so, if you want it to execute your command after reading only one line, you have to explicitly state it with `-n 1`.
And then, the final one ~~(i wrote it first though :thinking:)~~ is -I and what it serves basically is to "capture" the name of the argument, the {} *seems* to represent the name of the input that is read by xargs, though i think i understood that by example from a couple of tutorial/manual pages.

# Outcome #

```bash
[-- 27:45 -- zenandroid ~/Music]$ du -h mpThree mpThreeImp/
145M    mpThree
106M    mpThreeImp/
 note: mpThreeImp has the 27 converted mp3 files in opus format

[-- 43:35 -- zenandroid ~/Music/MBR]$ du -h .
100M    ./mb3
76M    ./obus
176M    .

[-- 02:19 -- zenandroid ~/Music/Moody_Music]$ du -h .
174M    ./mp3
126M    ./opus
324M    .

[-- 15:16 -- zenandroid ~/Music/Petar_Dundov]$ du -h .
61M    ./opus
81M    ./Ideas from the pond
142M    .

[-- 31:41 -- zenandroid ~/Music/SciFi_Ambient]$ du -h .
282M    ./opus
419M    ./notOpus
706M    .
```

The average percentage of the size reduction is equal to 72.8%
