---
title: "Loops"
date: 2019-04-16T17:53:57-04:00
draft: true
---

## by Matthew Barlowe

Loops are an important part of programming in any language. So in this
tutorial we are going to go over what they do and how to implement them.

In Python there are two typs of loops: the `for` loop and the `while` loop.
But before we get into the distinction of the two lets talk about why you want to use
loops in your programming.

# Why loops?

There's a phrase in programming you'll hear often if you keep pursuing this hobby/career,
and that phrase is, "Don't repeat yourself." It boils down to if you need to do the same thing
over and over again don't just cut and past the code or "write everything twice" but try to
abstract the process in to one block of code that just needs to be ran once. Or if you can't
do that then turn the code into a function that can be called when needed.

But why do this? What does it matter if cutting and pasting the code gets things done faster?
There are couple reasons behind this.

* **It's easier to debug.** If you only have one block of code to look at to find errors instead of
three or five or whatever you will spend far less time trying to fix it if it breaks.

* **It's easier to read** The smaller code is the easier it is to read and understand. Even if you
just work on code by yourself, trust me your future self will thank you for your consideration.

# Loops in Action

So let's say you wanted to print out "Let's Go" five times. Sure you could put `print("Let's Go")`
ten times in your script and run it and get the desired result. But following the ideas discussed
above we don't want to do that. This is where the `for` loop comes in. Lets look at some example code

    for x in range(5):
        print("Let's Go")

If you put that in a file and run it similar to what we did in the [Hello World]({{< "python/helloworld" >}})
tutorial it would produce this:

    Let's Go
    Let's Go
    Let's Go
    Let's Go
    Let's Go

So with a `for` loop we were able to reduce what would have been five lines of code down to two. In the
grand scheme of things is this trivial? Sure but it's a good habit to get into in the beginning because
its much easier to apply this philosophy at the start of each project than to go back and do it after
the code is written.

Let's break down exactly what the code did though. Ok the `range(5)` creates an ordered group of numbers
starting at 0 and ending at 4. Python always starts counting at 0 unless you tell it not to so just
reprogram yourself to think of 0 as 1. [It's easy not hard!](https://www.youtube.com/watch?v=VCcd5BsquPw)
So if it starts at zero then why did you put 5 in there? Why not 4? That's because the end range in a lot
of Python things is not inclusive. 5 tells it where to stop but it doesn't include it in the actual group
of numbers `range` returns. I understand all this is a bit counterintuitive and I still mess it up sometimes,
but with practice it will come naturally.


