---
layout: post
title: Vim plugins ? what do you think i am, a weakling ?
tags: vim
---

So, i recently began looking at my list of plugins in vim.

If i recall correctly i had :

* Vundle
* Vim airline, and the themes.
* LaTeX-BoX
* NERDtree
And then i asked myself, do i *really* need these ?

So i started doing a bit of research :

- Vundle ? Nah if i really wanted i can just copy everything into ~\\.vim or just follow the manual
  installation instructions on the Github repository.
- I also found out that the vanilla status line can very well be customized with enough commands,
  nothing too complicated if you invest an hour or two reading the documentation and looking at some
  examples.
- The LaTeX-Box one is that you can say i hesitated to remove, but i figured with enough google
  search i should be good to go, after all, i have all the MikTeX binaries i need right ?
- I found that Netrw can be a replacement for NERDTree, and it comes preinstalled with vim.

After pondering about this for a couple of days, i made a decision that i hope i wont regret.

## Result :

As a result of my reconfiguring everything, this is what i ended up with.
![top_10_anime_betrayals]({{"/assets/plugins.png"|absolute_url}})

# Wait, ... what ?

Well, let me explain.

The main idea behind my (perceived) need to remove plugins (or at least reduce them) was simply to
reduce dependencies, such that if i move to another environment, i would do A-OK with my own
vimrc.

Right ?

... right.

So i started looking up the status line documentation and sure enough, there's some interesting
stuff in there, and then moved to the netrw doc, and then all the other doc that was pertinent etc
... 

__BUT__

Then, i asked myself the same question i asked earlier.

Do i *really* need this entire process ?

Ever since i remember, i never really used any other environment, so this entire thing may not be
worth it at all.

Still, i found huge value in having at least some portable functionality to be available.
<small> <small> I will make a post or two about this </small> </small>

So i will still read the doc of status line more, and netrw, and what ever else there may be. (within
reason, of course)

But i'll allow installing a few plugins.

| No | Plugin             | Short description                     |
| -- | :-----             | :-----------------                    |
| 1  | Vundle             | Plugin manager.                       |
| 2  | NERDtree           | as a tree navigator                   |
| 3  | vim-surround       | Surrounding stuff with tags and stuff |
| 4  | LaTeX-Box          | Latex compiler/viewer                 |
| 5  | Tabular            | Text aligning                         |
| 6  | Vim-snipmate       | Shortcuts & snippets                  |
| 7  | vim airline+themes | Status line customization             |


And i'll probably add a few; namely ctags and other ones i'm forgetting right now.

> New users too often jump directly to a stereotypical config, borrowing most of their settings and
> mappings from other users and installing whatever plugins and plugin managers are trending. The idea
> is to skip most of the mostly imaginary but very frightening learning curve and be as productive as
> possible as quickly as possible.

> Of course, if they had taken the time to learn Vim properly, they wouldn't "need" all that cargo
> cult bullshit but who cares about learning? What matters is to have something, not to get it. Right?
   
From [romainl]("https://github.com/romainl/the-patient-vimmer/tree/gh-pages"), *the-patient-vimmer*

:thinking:

I will admit, i understand where he's coming from and i agree 100% with him, however right now the
`being productive as quickly as possible` is what's making me do this.

## Some clarifications:

Some of my plugins, espacially the non essential ones (airline/nerdtree/etc ..) will very probably
bite the dust soon, since when i'll find the replacement for them, i will just remove them, after
all, if i can get *ALL* the goodness i use while at the same time having less dependencies, why the
hell have it there in the first place.


### lol i have the lingering feeling that this post is a mess


# Vim plugins ? what do you think i am, a weakling ?
yes


# So i guess i'm going to be reading the patient vimmer :D
