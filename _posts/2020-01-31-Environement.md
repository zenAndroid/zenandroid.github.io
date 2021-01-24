---
layout: post
title: Mutation is a spook
tags: scheme sicp
description: Some further thoughts on why i like the Wizard Book, and elaborating on a recent AHA moment i had when reading section 3.2, the environment as a model of evaluation.
toc: true
---

![SICP]({{ "/assets/SICP.jpg" | relative_url }}){: .center-image } <center>The Wizard Book.</center>

This blog post (and general series of SICP posts) is dedicated in part to Zorua, in part to the future form of me, and in final part to you, **the spirit that is residing inside the computer.**

As you probably know if you've been reading my latest posts, I have just started chapter 3 of SICP, the chapter that talks about Mutation, States, and Objects (astute readers will notice that, indeed, that is the title of the chapter), and while i can't really say I'm that advanced in it (as i speak, the last exercise i "finished" (In quotes because there are still some cases my solution can't handle [^halting]) was 3.18.

I can of course go and try working on it some more until i get the general solution (the correct solution, to be fair), but i spent almost all day on it [^Well], and i legitimately couldn't think of a complete solution to it, so i simply decided to give myself a break (also since i want to avoid the trap i had with section 2.4 and 2.5; Staying essentially stuck in one place without the ability to advance because of my obsessive compulsive behavior regarding trying to complete the exercises SEQUENTIALLY, which i always realize was a complete misuse of my time *IN HINDSIGHT*) 

***Anyways ...***, so, about SICP.

I love SICP. *(So far)*

And i see a lot of people that share this sentiment.

However, I don't feel that this feeling is communicated clearly in the popular reviews i see about SICP.

I won't say much about this since i feel like I've already said enough, TL;DR : A lot of it i feel is not specific enough and too vague to produce any sort of cool and crisp mental image of the content of the book for the other person you're trying to communicate with.

Without further ado, some of the reasons i find SICP very nice :

- Does not teach the 'how' of computer science, teaches you the 'why'.
- Meaty.
- Assumes the best in the reader.

# Why though ? #

The impetus for writing this post was my reaction to [Section 3.2](https://sarabander.github.io/sicp/html/3_002e2.xhtml#g_t3_002e2), because i first read it and had the mild reaction of 'huh, okay neat', but as i started doing the exercises they kind of showed that i only skimmed the text and did not *grok* the content, and i had to think about it really hard to figure it out, then i had an 'AHA moment' that just makes me love the experience of reading this book.

What is this 'AHA' moment you ask? Well, for me, it boils down to this: Even though SICP might not revolutionize computer science and bring about new concepts to the field, it *does revolutionize the way you look* at computer programs and computer science in general, because it does not tell you, for instance, how type systems work and how you can conceptualize inheritance or something to that effect, it shows how these things come naturally by *having you build the system from the ground up*, and you come out of it having a deeper understanding of how it might be implemented in "real world" scenarios.

That's just one example in the end of chapter 2 by the way, and it seems that there's still a lot where that came from.

You can go ahead and read [Section 3.2](https://sarabander.github.io/sicp/html/3_002e2.xhtml#g_t3_002e2), and see if you gain anything from it, personally, what i gained was a clear understanding of how environments can shadow other environments and how its possible to model variable/name shadowing in a language, read that sentence again, this is what i talked about when i meant that my first reaction to it was a somewhat tame 'huh, okay neat', but when I thought about it,  this meant that i could start imagining how:
- to implement this whole environement business
- the interpreter "knows" the difference between a variable and a procedure (by checking if its simply pointing to a raw value, or by checking if its pointing to the special construct of <procedure-info, enclosing-environment-pointer>), how any procedure evaluation happens (the formal parameter gets substituted for the actual parameter in the procedure's body, and that is evaluated normally), how a local variable shadows global ones, and many other goodies.

> I am under no illusion that this is exactly how type coercion works for instance, the same way i am under no illusion that the number used in programming languages are built up using church encoding, but it does explain how they can be achieved using basic components which is the entire point as i understand it.

It does not teach you how to implement language feature X in your coding habits and exploit it to the max.

Rather, it ~~tells~~ ***shows*** you *why* you need language feature X in your coding habits and while doing it, naturally shows you how to do so.

## Tangent ##

I saw a bunch of reviews, most of them i liked and agreed with, but i always wondered: "Why aren't they citing concrete examples from the book, surely the reviewer's point will become clearer if they show which section lead them to this conclusion?" and that was my initial intent as well when planning my reviews, but then you soon come to a realization ...

# Meaty: This book has no filler #

Every chapter is necessary, every subsection is crucial, every paragraph makes you think, there is no easy way to compress the information held within the content ... So if you are an optimistic reviewer looking to show people why you think sicp is neat by going through a *truly* [^Footnote] exhaustive list of reasons, then you can only claim you've rewritten SICP in its entirety, which, at that point, you're back at square one, if they weren't going to read SICP, what makes you think they'll read your version of it ?

But i will try to formulate a sensibly detailed review of what i appreciated in SICP, I will try ...

# Assuming the best #

Reading SICP is good.

*Skimming* SICP is ***BAD***.

The exercises are the true soul of the book, I simply *cannot* imagine someone going through the entire book without struggling with the exercise and learning much.

And it has quite a decent amount of exercises too, ... And the difficulty curve isn't exactly ... Predictable either. [^lies]


For instance (trying to keep the non-exhaustiveness promise in mind). In chapter 1 you go form basically nothing to implementing a basic version of newton's method of calculating square roots and cube roots, to then use higher order procedures to abstract over the past examples to implementing *nth-root* methods, and essentially finding the roots of any equation using the binary search methodology, delving in the deep end of recursion and Fibonacci method, optimizing that further using tail-call-optimization, then jumping to prime number detection, implementing a *beautiful* probabilistic method to detect prime numbers *in a logarithmic number of steps*, and so many other things this blog post is too small to contain ...

... Like the fact that it has you *prove* some facts about *phi*, [the golden ratio]({{site.baseurl}}{% post_url 2019-01-02-New-year %}), and it has you write the definition of the tangent function and Euler's number in their continued fraction form and its *fucking glorious*.

And that's just the *first chapter*.

Then the second chapter comes and ... It brings its own set of mind blowing concepts ...

Like introducing the very important pair construct in lisps (`cons` and its natural extension `list`), and the use of that as a building block to create interesting things, they emphasize that everything that the outer systems have to see are abstract selectors that can be used without knowing the implementation details [^clarity], then the next section talks about having means of combination that allow for closures on types that are incredibly powerful tools for expressing more advanced ideas (TL;DR closure property means having a way to perform an operation on an object (or a set of objects) [^NotOOP] and getting an object of the same type), introducing the concept of mappings and accumulation, *IMMEDIATELY* shoving the reader down the deep end and telling them to implement [Horner's method](https://en.wikipedia.org/wiki/Horner%27s_method) using accumulations, then *IMMEDIATELY* combining these concepts (mappings and accumulations) to make you implement basic linear algebra operations (namely dot-product, vectorXmatrix, matrixXmatrix, and matrix-transpose), then another beautiful concept is introduced with the concept of nested mapping.

If you thought nested for loops are hard to come by in functional programming, think again, because each for loop body can be put in a one to one correspondence with a mapping. The new thing i should have realized is that mapping `(lambda(i) <loop-body> (sequence 1 n))` is sufficient to model the index, that helped put things in more equal footing in my mind.

And then, just in case you needed a "more" practical example, there is a Picture Language example that shows the beauty of the Closure property.

And no, chapter 2 still has a lot of goodies to offer, set representations and operations on sets, a basic implementation of a symbolic differentiator, a truck-load of examples about Huffman encoding, a very Out OF Character exercise where SICP asks you to encode the lyrics of a rock song with very interesting lyrics.

And finally, we close on Chapter 2 and let it rest, because there is no way it'll add something more it didn't add before ...

Well that was a scheming lie, because you see, chapter 2 still has a final mind blow to deliver in section 2.4 and 2.5 and it  comes when you implement a generic arithmetic system, with multiple types of data and generic operations that work across different types, making it so by following the exercises you have the power to represent polynomials whose coefficients are either complex numbers, regular numbers, rational number, or ... Polynomials themselves, and also the generic operations can work on multiple types as long as you design the corresponding type casters :)

The final extended exercise for chapter 2 is adding rational functions to the system .. And its about as amazing as it sounds.

That is the end of chapter 2, then there's chapter 3, which I am reading now.

# In conclusion #

SICP is pretty cool.



[^terror]:There is one `partial-trees` exercise/algorithm that was truly difficult, and **Truly** satisfying to debug/trace.
[^NotOOP]:Object not in the sense of OOP, but in the sense of 'a conceptual unit'
[^clarity]:Not exactly a new idea, but SICP always has this way of teaching, as i said earlier, that shows you *why* these things help you later on, and the fact is that you wont realize it if you don't stop and think about it, and that,s not a bug, *it's a feature*.
[^Footnote]:As opposed to these blog posts that don't delve deep into the subject matter ... Oh sure we *try*. But ... This is point of the paragraph, it's that we *can't*.
[^Well]:Not all day trying to do the exercise itself but rather i went on a personal tangent where i forced my self to *grok* the nature of pairs in LISPS languages, which was very productive if i say so myself.
[^halting]:TL;DR : I have spent a bigger amount of time than I'd care to admit trying to solve the problem of whether or not i can know if a function will eventually return or if it will loop, ... No i will not provide details it is shameful enough as it is, what do you mean you can cross reference the date of this post with my commit history pleas don't do that
[^lies]:Okay, technically, it is somewhat predictable.
