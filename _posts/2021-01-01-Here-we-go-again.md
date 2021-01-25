---
layout: post
tags: meta future
title: Repeat after me, comment after me, assemble before me!
description: Quick summary covering what I've done and what I plan on doing.
---

Not really interested in making a drawn out introduction post, I'm not going to bother.

## Why the disappearance this time, zen? ##

- My Linux kernel panicked, I found myself in a situation where I couldn't afford to really try and fiddle with it and fix it, and so I didn't.
- Just started using Windows because with college and such I couldn't afford the distraction (but I kept feeling a voice in my head going all *this is only an excuse and you know it*, I ignored it even though I knew it might have had a point ...)
- Anyways, months fly by, here I am now.
- I look at the Linux OS I had installed, it kernel panicked every time, and I did a quick estimation and remembered that there weren't really any interesting files in the Linux partition that I didn't have in the Windows install anyways, so I just ... overwrote the Linux partitions and installed something new, this time tho, I went with something different and installed MX-Linux, kinda new, and I guess I won't have i3 installed, but I wanted to not waste any time on that stuff and just *finish my initial work on SICP*, and long story short, I believe I'm at that point now, so that's good (I skipped a lot of stuff, but I might talk about that later, not that its particularly important though)
- I found out some interesting software and I still have some interesting ideas that I want to talk about.

## Weird title but OK ... ##

It's relevant I promise!

You see, I have a lot of things to talk about, but I don't think I'm going to talk about them in this post, rather I only want to talk about three things:
- I want to comment on my experience on using spaced repetition tools.
- I want to gloat about having implemented commenting functionality in this blog (yes, yes, I know, finally)
- And I want to recount my current progress with SICP :)

# SPACED REPETITION SOFTWARE, Polar, and an idea for an application:

There is this software I've been using called [Polar](https://getpolarized.io/) that I discovered and it's basically advertised as a document repository, where you can put your PDF documents and EPUB as well, it supports annotating the documents and adding comments to the annotations.

But that isn't what convinced me.

It can integrate well with Anki, because:
- You can create cloze deletion flashcards as well as Basic QnA flashcards from your highlights.
- You can then click a button that syncs the cards up with Anki, tagging the card with `deck:nameOfDeck` will create a card in the `nameOfDeck` deck in Anki.

Sounds good, ... and indeed I've been using it and I will continue to do so ...

But there are some aspects of it that I don't care for at all:
- It is an electron-based app, and what is worse, it only works if you are online [this is disgusting], and it seems to be entirely based on the cloud, so it feels sluggish.
- There are some limits on the storage and on the web captures ... this is unfortunate and disgusting as well, although I guess I can see why that is the case, what with the entire infrastructure being on the cloud and all, even then I feel like it is a bit too restrictive, the cynical ~~assh~~person inside of me tells me that it might indirectly incentivize people to get a monthly/whatever subscription.
- IT JUST FEELS BLOATED AND SLUGGISH AND ... BLEH.
- I don't like the fact that when there is a string X of text on a document, I have to highlight it first, *THEN* I get to create flash cards off it, and I would like it if there was an option to make it so that each highlight automatically becomes it's own excerpt-like flashcard.
- When in the main menu of documents, clicking on a document, opens *another* window for the document, instead of opening the document in the same window, which just reinforces my disgust.
- ITS ON THE CLOUD, *THE CLOUD* AND IT DOESN'T EVEN CACHE YOUR DOCUMENTS, AT ALL, SO EVEN IF YOU USED A DOCUMENT 5 SECONDS AGO BUT YOU LOST CONNECTION ALL OF A SUDDEN YOU CAN'T ACCESS THAT DOCUMENT *AT ALL*, THIS IS PERVERSE !!!

The problem is that It seems to me that there are like, two people working on this, maybe just one, the other person providing a helping hand.
And like, I get it, there seems to be a mountain of things/bugs to fix, but there seems to be no end of it, and I just want to see if I can do something better.

Is it going to be electron though? I don't know ... But it seems that PDF.js is doing a lot of the work of rendering and such and I'd prefer spending more of my time thinking about domain related issues.

Doesn't help that I don't know much JavaScript myself ...

In any case, even after all of the constructive criticism up above, I am thankful for this software because as far as I'm concerned it more than makes up for any software related pain point I have by effectively allowing me to Implement my own flavor of incremental reading,... although, I have to say, the fact that I *avoid* your app as much as possible isn't a great sign chief ...

Ultimately it is caused mostly by their having different "goals" for the project, and I guess I can't criticize them too much.

But *if* I manage to get this off the ground, there are definitely a couple things I will address:
- Well, I won't have accounts for one, no cloud shenanigans either ...
- The app itself, as I envision it, will work purely locally and the user will feed it a document which it will then process, as in there *probably* won't be a 'repository' as such. Not sure about this point though.
    - Well, maybe I could do something like 'hey point the app to your "local repository folder" or something' ...
- I wonder if I should provide the functionality to create flashcards from *within* the app, or just turning the highlights into text excerpts as Basic cards with the excerpts on the front and nothing on the back ...
    - Well, in any case, I will probably think some more about this, most likely I will only provide for Clozes and Basic cards though, and I don't even want to think about images in cards right now.
- Tagging functionality .... is ... well.. it *probably* won't hit the first version because to be honest I can't think of some way to do it off the top of my head, maybe it will change if I carefully think about it though (a part of my brain is telling me that is basic development, ¯\\_(ツ)\_/¯ alright then ... I'll think about it)

I think that's it ?

Probably the most annoying things at least ...

# Utter your words, mortal 

Commenting functionality has arrived, with the help of this most [wondrous software](https://utteranc.es/) that allows me to have commenting functionality which is the functionality I have been looking for, for a long time.
I love that functionality very much.

So .... yeah, it was actually a lot easier than expected to be honest.

If I recall correctly, it requires you to give the utterances bot permission to create and manage issues (because basically comment threads are issues in the GitHub repository, and followup comments are child comments on that issue, although this can be changed), and then there is a script you add to your template where you put the commenting section where you want it to be, and VIOLA.

Not perfectly ideal though, since it requires commenters to sign in using their GitHub account, which I imagine isn't the case for everybody.


But still, ... kinda neat little open source software that does the task as it's supposed to, which get a thumbs-up from me.
