---
layout: post
toc: true
title: Manjaro everybody!
tags: manjaro dual-boot
description: Post install ramblings, thoughts, and plans, and a discussion between two people that are actually the same person.
---

# The install #

Hello future zenBoi, I am writing this post from the manjaro install.

Be happy friend, you have solved a great problem.

Or rather, you have solved a great **META**-problem.

But first, let's talk about the result of your cowardice.

## Partioning fears ##

You have chickened out from trying to install Manjaro on separate (by separate i mean, of course, non-contiguous) partitions, and you have then shrinked your Windows partition such that the install resides on three contiguous partitions, you have also respected your oath to divide the install into three partition:
- The home partition.
- The root (/) partition.
- And the swap partition.
(The swap partition will probably largely go unused, we both surely agree, but oh well, it's not like those 16 Gigs are going to be that important, am i correct in positing this statement or what? haha...)

## Immediately post-install ##

You remembered when you last installed Manjaro, you had connection issues, something about your OS being unable to detect WiFi or something, you noticed that your install does indeed connect to the WiFi, and you thought that the gods must have saved you from the hassle.
The gods laughed at you as you praised them, for you see, as you soon found out, you were *WRONG*.

You, thinking that you were safe, went to visit an forum thread that you created, thinking you will be amused at the misfortune of your younger self, so you went ahead and visited [it](https://forum.manjaro.org/t/wifi-does-not-work-after-suspend-driver-rtl8723be/47354), that is the fateful moment where your mind realized that you were *WRONG* when you misremembered your previous install issue, for it is not the problem that the OS does not detect the WiFi at all, it is the fact that *after you suspend your laptop, the WiFi card does not detect WiFi anymore*.

Fear seeped into your body and your orifices as you realized the potential significance and danger of the ramifications of this fact.

So you had to be a rational person, marry the scientific method and test your hypothesis.

1) You turn on your install.
2) You are connected norally to your WiFi.
3) You suspend your laptop.
4) You resume it.

...

The results were what you feared all along, this is a failure, a catastrophe, truly the proverbial end of the universe.

## That DAMNED RTL8723BE DRIVER ##

YOU RAGE AGAINST THE HEAVENS AS YOU REALIZE THAT [YOU PREDICTED THIS](https://forum.manjaro.org/t/wifi-does-not-work-after-suspend-driver-rtl8723be/47354/48?u=zenandroid).

It is that damned hardware incompatibility again, how shall you solve it ? is it going to require some low-level tinkering ? some [source-code recompiling of the drivers themselves ?](https://github.com/lwfinger/rtlwifi_new).

You were as horrified as i am right now at the prospect of trouble-shooting this issue.

You wanted none of it.

You rEEEEeEEeEeeeeed like you've never reEEeeEd before.

## Losing hope ... ##

This is the point where you started making some assumptions about the level of worth of the install.
The most obvious (to you, at that particular moment) was that a WiFi-less install is worthless, why waste your energy with it then.
Such a waste, and you hesitated when you thought that you should scratch the whole thing and nuke it from the partitions and just stick to the Virtual machines.

...

But you sticked to your oath my boy, and you didn't uninstall it just yet.

~~I am getting tired writing this fucking post this way but i started it and i'm gonna finish it.~~

Maybe it'll fix itself this time if i recompile that github thing this time, you thought, still hopeful.

But you do not do that, and you just try surfing the web and checking it out normally, open-mindedly ...

And that's where you noticed it ...

# Hmm #


"Hmm, such a shame, this install seems extremely stable otherwise, before i suspend it, it works amazingly , too bad i have to do that .. often ..", you think.

But just as you utter it, you notice an incongruity in it.

"Hmm, let me thonk for a minute, ... *do i really suspend that much?*"

Why yes, of course you do, just think of all the times you close the lid of your laptop.

"I guess that is true, but i can just get used to .. like .. *not doing it* you know ?"

Hmm, go on.

"So, this system is stable as long as it is not suspended right? so we just wont suspend it, easy as that"

"And hell, we'll just change the hecking seting on the power manager and tell it not to suspend the damn laptop if we close the lid, and just .. i dunno, turn off the brightness or something ... "

"I see you're hesitating and i understand, it feels like chickening out and working around the problem .."

"But, dude, you *tried* okay ? like I *am* you, I know the stuff we went through, we tried reading the man-pages, fiddking around with the options, fiddling around with module config files, *nothing worked* , *NOTHING*"

You have a point.

"I know, and like *dude*, maybe *now* things have *changed*, I mean maybe now the system parses the config files *differently* or otherwise does stuff differently such that making modifications will *actually* work, but *before* trying that at least make this test, it costs you near-nothing to do it, so why not, ya know?"

Hmm, good point, but stop using italics they are an *eyesore*.

"So go ahead, this might turn out to not be that big a problem after all".

Perhaps, and, sorst case scenario, If i ever *do* suspend it, I'll just .. reboot it ?

"Sweet, I see you've started adapting this mode of thought"

# Back to future time-line zenBoi #

That is the **META**-problem i was talking about, and i am very proud of you for having finally defeating that trap.

The result of this will be even more apparent with the next posts you shall post.

## Resulting decision ##

Firstly, rebooting this system takes less than a minute and a half (slightly close to ~1:20).
Secondly, the 'change power manager setting to do another action when you close the lid' trick is really neat.

# Yay #
 Now i don't have to cripple myself to death and can use this otherwise awesome system the way i please it.
