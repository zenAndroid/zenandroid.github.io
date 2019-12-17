---
layout: post
title: Can't stop, won't stop
tags: meta future help-me
description: It's a disease, and now i've understood the cure, or maybe the thought that i have understood the cure is part of the diesease ? idk ... like how people who are addicted always claim that they can stop doing whatever it is they are doing ? oh no i just spooked myself.
---

# How far does the rabithole goes ? #
 We may never know.

## Status update ##

Finals over, still have to finish up an assignement.
Manjaro install looking good, tho i encountered a couple problems.

#### pulse_audio ####
The audio didn't work at first, thought it was a weird thing, stareted looking around and seeing what I could do, I thought it'd be easy at first,so I started looking at the local configuration I had and seeing if I could fix it by tweaking things aroud, didn't work though.

However, after skimming the web for a while I ran ``sudo install_pulseaudio`` and it worked !!!

NEXT.

#### nVidia Drivers ####

You know I'm all about that FOSS software right?
wrong lol
Anyway, when I was trying to install the proprietary graphic driver ...
![Yes]({{ "/assets/mhwdAnticipate.png" | relative_url }})

I click ``Yes``, obviously, and then this happens;

![SadCat]({{ "/assets/mhwBad.png" | relative_url }})

Well, well, well ...

So yeah that kinda pissed me off, I wanted to fix it, but then my **PREMATURE MICRO-OPTIMISATION ATTEMPT** alarm revved up.

So I vowed to fix it when I'll have the time^TM.

#### SCREEN TEARING ####

NOW THIS IS PISSING ME OFF.

AND IT'S ACTUALLY SO IMPORTANT I LITERALLY NEED TO FIX IT. ASAP.

So, when I just installed this and had firefox on it, I had no problems with using firefox whatsoever.

But suddenly I notice annoying screen tearing in the browser and in videos and it's incredibly annoying.

Worse yet, when I try and go fullscreen, the firefox display just freezes completely.

Sadly (NOT REALLY LOL) this is probably going to need a fix for the problem I outlined earlier about nvidia drivers ...

#### Muh minimalism ####

Not quite an issue but just an attempt at PREMATURE MICRO-OPTIMISATION, ...

I was thinking I'd get rid of the bookmarks toolbar on firefox, in order to gain more screen space, and access the bookmarks myself (by figuring out where firefox keeps them) pipe that output to dmenu or something like that in order to automate it.

But again, not that important.


# 17:11- "solved" my nVidia issue #

wrote that at 12:53, now i solved it, just two commands really, i removed the old one and installed the new one.

... not much troubleshooting happening here heh, ... well, good for me i guess ...

