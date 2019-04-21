---
title: "Loops"
date: 2019-04-16T17:53:57-04:00
draft: False
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
```python
for x in range(5):
    print("Let's Go")
```

If you put that in a file and run it similar to what we did in the [Hello World]({{< relref "python/helloworld" >}})
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
but with practice it will come ... well not naturally but you'll only mess it up half the time instead
of all the time.

So the `range(5)` gives us what we are going to loop over. As you learn more about Python you'll see
that `range(5)` is just one of many things you can loop over. The other part of the sentence `for x`
is where the looping happens. `for x` is actually saying "for each item in `range(5)`", the `x` is just
a variable for that item. You could replace `x` with anything:
```python
for x in range(5):
    print("Let's Go")

for number in range(5):
    print("Let's Go")

for thingy in range(5):
    print("Let's Go")

for Bob in range(5):
    print("Let's Go")
```

All those blocks of code will produce the same output shown above which is five lines of "Let's Go."

Think of `for` loops as having a bag of marbles. And like in code you can't do anything else until
you pull every marble out of the bag.  In this analogy `range(5)` would be our bag of marbles and `for x`
would be the act of us pulling each marble out at a time. The `print("Let's Go")` would be what we do
each time we pull a marble out of the bag. So the process would be pull a marble, do something, pull a marble,
do something, etc. until you ran out of marbles. That's a real word equivalent of what we just
told the computer to do with our `for` loop above.

The real power of Python `for` loops happens though when you need to do something to each
marble you pull out of the bag. That's where the `for x` part comes in. By assigning each item
in the collection to a variable we can do things with those variables as we loop through the collection
For example:
```python
for x in range(5):
    print(x)
```

Which produces this output:

    0
    1
    2
    3
    4

We can print them, perform mathematical operations on them, store them in file for safe keeping etc.
`for` loops are a tool that is indispensable not only in Python but in all programming languages as
they form a core concept of programming and computer science. One key aspect though of the variables
we create with a loop is if you have that variable name storing a value somewhere else in your code
the loop will override that value with the last value it has from the loop. For example:

```python
x = 10
for x in range(5)
    print(x)
print(x)
```

The output will be:

    0
    1
    2
    3
    4
    4

The value of ten will be overwritten and gone.

# While Loops

`while` loops are a bit different than `for` loops. `for` loops will end when the amount of items
they need to loop over is exhausted. `while` loops will continuing looping until a certain logical condition
is met. Which is why you have to be careful when using them because thy can continue forever creating
a condition called an infinite loop that will never terminate unless you force it to. If your program
does this usually a `Ctrl+C` is the break signal for most computers to stop running things and if that
doesn't work you can always restart.

While loops look like this:
```python
    x = 0
    while x < 5:
        print(x)
        x += 1
```
As you can see the conditional statement in this `while` loop is `x<5`, and as long as
`x` continues to be less than 5 the loop will continue repeating. That's why we have to add
the line `x += 1`[^1] in there to increment the value of `x` each time the loop repeats. If we
didn't do that then the loop would continue forever.

#Summary

Ok lets wrap things up. One last thing about syntax is that both `for` and `while` loop
lines must end in a `:` or else Python will get angry and yell at you.

* `for` loops
    * Loop over a collection of items passed to them and performs some code until colleciton is exhausted
    * As the loop progresses assigns each item if pulls from the collection to a variable
    which you can then use or ignore
    * Has the syntax `for x in collection:` where `collection` is the items you want to loop
    over and `x` is the variable you assign the piece of the collection the code pulls in that
    run through the loop
* `while` loops
    * Loops over a set of commands until a conditional statement is met.
    * Any variables use in the loop statment are usually assigned before the loop statement
    and not in the loop statement unlike `for` loops.
    * Has the syntax `while condition is true:` where the condition could be `x=10`, `sky='blue'`
    etc. The condition is whatever you want it to be.
    * It is very easy to create infinite loops and must use caution in creating `while`

This page is on [Github](https://github.com/mcbarlowe/website). If you see errors feel free to
submit a pull request or contact me on [Twitter](https://twitter.com/barloweanalytic) or email
[barloweanalytics@gmail.com](mailto:barloweanalytics@gmail.com).




[^1]: `x += 1` is the equivalent of `x = x + 1`. You can also do this with other math functions
    such as `x -= 1` which is the same as `x = x - 1` or `x *= 1` which is the same as `x = x * 1`.
    There is no benefit in using one over the other other than to save keystrokes and keep know it
    alls on Stack Overflow from trying to uneccesarily improve your code even though you didnt ask
    them to.
