---
layout: post
title: An experiment in C++ multithreading.
tags: cpp
description: In which i tell you about that time i decided to make life a bit more complicated by redoing an assignment i had in a language i am not entirely familiar with using a paradigm pretty much unknown to me, welcome to zenBlog.
toc: true
---

# Introduction #

In my last semester, our OS design teacher gave us an assignment to do at the end that revolved around synchronizing threads and so on.

## Assignment description ##

We were tasked with simulating a train station that had 3 stations, 3 tracks, 6 trains, and 2 trains per track.

A train's sole behavior is going forward in the track, NO LOOKING BACK.

The mutual exclusion part comes from the fact that, of course, no two trains can occupy the same `Cell`. (a track is made out of a bunch of `Cell` objects ...)

Oh, also, we needed to implement it in Java, so ... Yeah ...

# The assignment solution #

We (what me and my partner ended up doing (although to be honest he did most of the programming because at first i kind of did not understand semaphores and ended up procrastinating)) ended up with a solution that roughly did something like this:

- implemented  `Train`, `Cell`, `Station`, and `Track` classes.
 - Cell represents a portion of the track that can be occupied by a train, its most important fields, a semaphore protecting the cell, other than that the crucial function in regards to this application (if you can call it that) are: **enter** and **leave**, to model the actions a train can take.
 - A Station is a special Cell.
 - A track is a bunch of Cells.
 - Train had some private field like the train name, but the most important thing in this class is the thread its going to run, and, since this is Java we're talking about, this class naturally inherits Thread (I mean personally i would've made it *implement* the *Runnable* interface, but hey, that's just me, and i have to obey the instructions given to me ...) and the run() method is arguably the most central/crucial part of the application.

## run() ##
So, the functionality implemented in this method is actually kind of simple, but it's crucial to understand nonetheless :

1) The train calculates the next position.
2) It selects the corresponding cell from the array of the Track.
3) It locks the semaphore of that Cell
4) It enters the cell and does its business.
5) It leaves the cell
6) It releases the semaphore.

That's ... Yeah that's pretty much it.



# Thoughts on the Java solution #

So, i thought on providing the actual code, but i think it's way too much effort to paste it here and make sure its well formatted and then *translating* it.

So i won't bother, i will just be making this comment :

I felt the entire thing was a hard-coded hack and i was not pleased with it, the constant number of trains, the way the constructors was made ... Just ... I don't even think objects are necessary to be honest ..

Plus, i wanted to have a better understanding of the way things worked ... 

And so, i decided to try implementing the assignment in a language that i haven't touched in quite a while (certainly more than three years).

I have decided ti implement it .. ... (suspense builds ~~before you remember the title of this post~~)

# ... C++ #

So, let's get right into it:

- One source file and one header file per class.
- One main.cpp file.

That was the initial plan, anyways ...

## The classes ##

Train, Track, and Cell.

Just those three classes, my idea was that i can control for whether or not a cell is a station or not using a boolean ... ~~bad idea~~
Other than that, the train and track classes overall have the same functionality.

### The header files ###

I don't think i will be citing all the source code, ... but i think i should at least include the headers.

#### Train ####

```cpp
class Train {
public:
    std::string m_trainName;
    int m_initialPos;
    int m_currentPos;
    Track * m_associatedTrack; // Declaring this as a pointer makes me feel like i might make this harder for me than is necessary
    std::thread m_circulate;
    // -------------------------------------------------- //
    Train();
    ~Train();
    Train(int, Track *, std::string);
    void circulate();
};
```

#### Track ####

```cpp
class Track {
public:
    int m_trackLength;
    std::vector<Cell> m_actualTrack; // 2019-12-22 15:05 zenAndroid -- Just decided to turn this into a Cell-pointers vector
    // I can see the bullet hole in my foot already
    Track();
    Track(int, Cell, Cell, Cell, int, int, int);
    // This Constructor is a fucking disgrace, however i'll run with this at first then i assume i'll set up a map or something ...
    // Although I don't even fucking know if that'd be a decent way to solve it.
    // Still, better than fucking hardcoding it in the constructor, I bet.
};
```

#### Cell ####

```cpp
enum class CellType { CELL = 1 , STATION };

class Cell {
public:
    std::string m_cellName; // Guess
    CellType m_type;
    // Mutex protecting the *specific instance* of the cell.
    std::mutex* m_cellKey;
    // ----------------------------- //
    Cell();
    Cell(CellType);
    void promoteCell(std::string); // Upgrading a cell to station level.
    void enter(std::string); // Enter and leave this cell.
    void leave(std::string);

};
```

##### Everything's public, that's not exactly the, uh .. ideal way #####

~~*shrug* I mean, given the atomic nature of this personal project (literally just me working on it), i thought that I'd do it since i can manage to recall the source code all in my head, so there should be no problem with declaring them as public fields, and i didn't think too much about it, but ... it *does* make me wonder .. what's the point of private fields?~~

~~Presumably to protect the field such that you would have to create a getter/setter pair for it ... but how does that stop someone from fiddling with a field if they wanted to? Can't they just write to it using the setter, and likewise read from it using the getter ?~~

~~Maybe it's to prevent errors while testing or something?~~

~~I'm sure I'm missing something.~~

## Back to our topic ##

Anyways, the Cell class has the ``std::mutex* m_cellKey;`` field, which i did because when i tried the normal declaration, at the header making statements like ``std::mutex m_cellKey`` the compiler kept complaining about how std::mutex was non copyable and non movable, decided to try this pointer declaration method, it stopped whining, and here we are.

~~Will of course ask around to figure out what the heck that was about, soon~~

Train class hes a pointer to the associated track, because this isn't Java, so yeah you have to do this stuff.

~~Still don't understand why people hate pointers and such, they are difficult when they get hyper-hyper indirect and such but ehh~~

Also, i have just realized that my application leaks quite a bit of memory since I'm not freeing my pointers, ...

Will fix.

Also unlike Java, instead of the class inheriting directly from Thread/implementing *Runnable*, i had and `std::thread` as a field of the class, which i initialized in the constructor, and `.wait()`ed for in the destructor.

I have initialized the thread with the `circulate()` function, I will of course go in more depth about it.

Track class is straight forward, length of the track and the actual array holding the cells.

## circulate() ##

```cpp
void Train::circulate() { //  The functionality of the thread spawned by the instance of the class
    while(1){
        // TODO : something
        // Need to calculate the next position the train is going to take.
        m_currentPos = (m_currentPos + 1) % (m_associatedTrack->m_trackLength);
        // This is how you access the corresponding cell : m_associatedTrack->m_actualTrack[m_currentPos];
        // For now I don't want to confuse myself so I'll be doing the oprations chained together
        // until i grasp how i can do stuff like Cell = [that statement]; without hecking myself up
        //
        // ... Let me think
        m_associatedTrack->m_actualTrack[m_currentPos].enter(m_trainName);
        // Presumably enters the cell
        m_associatedTrack->m_actualTrack[m_currentPos].leave(m_trainName);
    }
} // 
```

Huh, as I am writing this blog post I am realizing what I've programmed isn't all that impressive ...
<b>Oh well.</b>
Wonder why this seemed like a more impressive thing in Java.

Anyways so yeah, the circulate function does what i outlined it doing before.
Although i might have to remove the leave function, given that when the train finishes the enter() function then it pretty much left anyways, and there is no need to clutter up the code and make the 1-to-1 correspondence to real life harder that it is.

Did that make sense ?

It didn't make sense huh?

What i mean is that i aim to make the code as accurately representative of reality as possible.

Because i think that'll actually make it easier to understand.

IE i want the code to model reality as closely as possible.

#### m\_circulate = std::thread(&Train::circulate,this); ####

The way to initialize threads is not completely intuitive, but i found [this answer](https://stackoverflow.com/questions/29814233/how-to-use-stdthread) on stack overflow.

Rubs me the wrong way when i take code from the interwebs and patch it in without understanding it, so I headed to cppreference to understand what i just did.

thread() noexcept; (1)                                                                         (since C++11)
thread( thread&& other ) noexcept; (2)                                                         (since C++11)
template< class Function, class... Args > explicit thread( Function&& f, Args&&... args ); (3) (since C++11)
thread(const thread&) = delete; (4)                                                            (since C++11)

So, obviously (~~wasn't actually obvious to me~~) number (3) is applicable here.

But yeah, TL;DR :: that constructor takes a function and an arguments, and it takes them by reference (or something .. :sob:)

Rules out initializing a thread with a function that takes an argument, so you pass in a function that takes none, and you put the arguments as class fields, with would be accessible since you're passing `this` too.

All right, i don't see how to expand on this any further.

## Planned improvements ##

- Add new class Station.
- Initialize the tracks with an std::map, rather that hardcoding it.
- See if you need classes and OOP at all (i suspect not).


# Conclusion #

In conclusion, this isn't the end, i will come back regularly to improve on this codebase.
I am glad i did this, I walked into this not knowing much about how to do multithreading in C++, and walked out with some semblance of an idea, while i am not under any illusion that i know much about the topic, i can at least say how to create the equivalent of a synchronized block in C++, and how to initialize a thread, which i am grateful for.

As of this writing, i am on this [commit](https://github.com/zenAndroid/i-like-trains/tree/e18268dde0a3c02035852f3aaf47e1ce51562d30) in my github [repository](https://github.com/zenAndroid/i-like-trains/).
