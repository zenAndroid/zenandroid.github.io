---
layout: post
title: Things and stuff
tags: meta
description: Twas a real struggle back in the day my friends, or maybe i was just too foolish to know how to behave myself correctly, but i like to believe the first alternative.
---


So, i was going to start playing around and talking about my "projects" not concerning this blog ( in other words, *moving on with the damn blog*) but things kept on coming up so I've decided to talk about the technical stuff concerning this blog first to get it over with, (well, for the most part anyways).
### The idea :
Thought about how i always wanted a blog, started looking around and thought WordPress was a good idea, then suddenly i remembered that Github pages was a thing, still hesitant i looked around how to go about this, several long and tedious hours later, here we are !

### The beginning :

Well, i started reading this [blog post](https://www.smashingmagazine.com/2014/08/build-blog-jekyll-github-pages/), did the thing, then after forking the thing and setting up my 'blog', i quickly realized that i didn't exactly want to stick to the theme available there, i wanted to change to something else called 'Hacker theme', and the tutorial didn't show a way of doing it which was ... ~~retarded~~ a questionable decision coming from the maker of that tutorial, so now i had no tutorial to follow, guess i'll just read the tutorial or the official jekyll docs right ? 

~~Abandon all hope, ye who enter here~~

The tutorial said that i could change the theme by going over to the settings and changing it on a scroll down menu. 

Well, ... i tried that, under different iterations (locally with modifying `_config.yml`, hosted with same setup, .... ), and well, __it didn't work__.

I am oversimplyfying it a ~~lot~~ bit because otherwise this post would be even longer but i think the following image can be a pretty good summary of what i felt at the end of this laborious process :).

![My impression]({{"/assets/discord-message.png" | absolute_url }})

Yeah, i gave up doing a blog altogether, but of course that didn't play out since someone is reading this, ... Well hopefully i mean.

So, I'm really really *REALLY* really really __really__ angry at jekyll at this point but not just because i didn't find a way to make it work, but also because i feel like i wasted such a big amount of time (~2 days basically) when i could have gone to do something more interesting (at the time i wanted to make a LaTeX template from my digital dream journal, and I'll ~~probably~~ definitely talk about it in one post and i assume I'll change that last string into a link ;]), but something inside of me just didn't want to give up on all of this.

### Poole/Hyde/Lanyon :

I stumbled on [a video on YouTube](https://www.youtube.com/watch?v=bty7LHm14CA), "How to install Jekyll themes", the person on the video talked about this Lanyon theme that i kinda like and so i went and did kind of the same thing (instead of the whole `gh-pages` branch i stayed with master since after all, it's not a project page but a full-fledged blog I'm after), then i tested the same thing for another theme that's from the same author, and it is of course Hyde.

I ended up preferring Hyde, so i forked it and customized the pages that i could customize and well, i began doing what i mentioned back at [Structure and Links]({{site.baseurl}}{% post_url 2017-12-24-First %}) which is all cool and good.

Then all that came after really are some minor changes here and there.


### The plans :

Hmm ...  What i plan to do ????

:thinking:


Well next thing is probably going to be writing the About page.
<small> Yeah, i bet that's the first time you heard about that huh ? </small>
:smirk:

And then, but this is __very__ secondary, is probably reading up on the CSS files and seeing if i
can modify some stuff. But that is very uhmmm well not urgent.

#### EDIT :
Also, i think, but again this is also secondary, might add google analytics ( ??? )
perhaps.
And i think I'll optimize the related post algorithm.

Let me explain.

So, for now related post just lists the 3 last posts.

That's it.

That's literally all that thing does, which is far from i imagine it to do, à savoir listing posts that only belong to the same category or something like that.

#### EDIT :
Also just had the idea of changing the layout of the posts (aka changing `_layouts/post.html`) so i include the word count of each post, to have a general idea of the length of post; i admit it's sort of pedantic on my part, but I'm only doing it since it's such a simple addition (god bless jekyll liquid tags)
