---
title: "Functions"
date: 2019-04-17T20:51:24-04:00
draft: false
---

### by Matthew Barlowe

What is a function? Basically ["a function is a block of code which only runs when it is called."](https://www.w3schools.com/python/python_functions.asp)
But what does that mean? It means that you have set aside a set of code inside your overall program
that won't run unless you specifically tell the computer that you want to run it. Still doesn't make
sense? Let's look at it in action. Create a file let's call it `test.py` and add this code to it:

    def our_function():
        print("This code is our function")

    print("This code is not our function")

Ok lets talk a little about the syntax before diving in deeper about how the
code works. In python functions are declared using `def` (short for define) which
tells Python we are declaring a function. `our_function` is what we want to
call the function and the `()` will tell what parameters we want to pass
to the function. In this case there are no parameters but you still need the
`()`. The `:` is also required at the end of every function declaration just like
with `for` and `while` loops. Also all code inside a function has to be indented
four spaces to tell the Python interpretor that those lines of code belongs to the function
just like you have to do with loops.

So if you ran that code what would expect the output to be? If you said just
`This code is not our function` then you would be correct. Python effectively
ignored our function when it runs the `test.py` file because we didn't **specifically**
tell our script to run that code. So how do you tell your script you want to run
that function? You do so by doing what's known as  "calling the function." This is
done by simply typing the functions name like this `our_function()` in your code.
For example:

    def our_function():
        print("This code is our function")

    print("This code is not our function")
    our_function()

If you run that script now you will get this output:

    This code is not our function
    This code is our function

# Function Parameters

What are function parameters? Function paramaters are values you pass to the function
whenever you call the function in your code. You normally pass the function paramters
because you want to do something to them inside the code of the function.
Our function above didn't have any paramaters because there was nothing in the `()`
when we decalred the function. But lets look at a function with parameters:

    def new_function(x, y):
        print(x*y)

    new_function(6,3)

What do you think the output of our new function will be? If you guessed `18` you are
correct! In this case our parameters are `x` and `y` in `new_function`. So when we
call the function what we put inside the parentheses becomes the value of the parameters
of the function. The values are assigned in order as they are passed to the function call
so `x` is equal to 6 and `y` is equal to three. If our function was declared like this
`def new_function(y, x)` then `y` would be equal to six and `x` would be equal to three.

This is an important concept to remember when passing parameters to a function. If you don't
pass the parameters in the correct order to the function call then the outputs will be
incorrect.

# Function Return

So you created a function and you passed it parameters to do something to, but what
if you need to get the output of what your code does and store it in another variable?
This is where the `return` keyword comes in. Using our above example:

    def new_function(x, y):
        print(x*y)
        return x*y

    x = new_function(6,3)
    print(x)

What do you think the output of this script will be? If you guessed this you are correct

    18
    18

As you can see the function prints out the value of `x*y` and then returns that value
when has completed running. We take that value the funciton `new_function` returned and
stored it in the variable `x` and then printed the value of `x` which is another 18.

One quick thing I want to touch on before we move on is the fact I use `x` as a variable twice
in this example. Are they the same variable? No they are two completely different
variables. The `x` variable that is the function parameter only exists within the function
itself. This idea is known as the variables scope. The scope is the area in which a variable
can be used, any use outside that area will result in an error. Try running this code:

    def new_function(x, y):
        print(x*y)
        return x*y

    new_function(6,3)
    print(x)

Which will produce this output:

    18
    Traceback (most recent call last):
      File "test.py", line 6, in <module>
        print(x)
    NameError: name 'x' is not defined

Even though we create `x` and assign it a value when we call the function, that variable only
exists inside the code of that function once we try to use it outside that scope Python throws
and error. Scope will be very important in the next section.

# Functions in Functions

Yes you can have funcions inside your functions, and if you wanted even functions inside those other functions.
Here's an example

    def math_function(x,y):

        def add_function(x,y):
            return x + y

        def subtract_function(x,y):
            return x - y

        return add_function(x,y), subtract_function(x,y)

    x, y = math_functions(6,3)
    print(x, y)

What do you think the output of this would be? If you guessed `9 3` you are correct. There's
a couple new things in this one I want to touch on before we continue. A function can return as
many things you want it to just seperate the values with a comma in the `return` statement as seen
in `return add_function(x,y), subtract_function(x,y)` and then you can assign them to individual
variables seperated by a comma as seen in `x, y = math_functions(6,3)` where the first variable
will be the first value returned, the second variable the second value etc.

As you can see here we created functions of `add_function` and `subtract_function` inside our
larger `math_function` function. But remember like the `x` variable above the `add_function`
and the `subtract_function` only exist inside the `math_function`. You can't call them in the main
part of your script without getting an error. If you wanted to be able to call them anywhere
in the file you would need to define the outside of the `math_function` like so:

    def add_function(x,y):
        return x + y

    def subtract_function(x,y):
        return x - y

    def math_function(x,y):
        return add_function(x,y), subtract_function(x,y)

    print(add_function(6,3))
    print(subtract_function(6,3))
    print(math_function(6,3))

One last thing is that you shouldn't variables inside the scopre of your function like I did
in the example above. You technically can but its considered bad programming form as you can easily
confuse what the variables represent at any given time in the code and makes it hard for others
to read.

# Overview

Functions are a key part to becoming a better programmer. But now that you know the how let's talk
a little about the why. Functions help programmers follow the "Don't Repeat Yourself" paradigm discussed
in our [loops tutorial]({{< relref "loops" >}}). They allow you to run a set of code over an over again
without having to manually type it out every time. Functions also allow us to name a set of operations
so that we know what those operations do without having to read the source code of the function. Like
our example you may not know what exactly was in the `add_function` but you could sort of figure out
that by its name the function did some sort of addition. This is also why using intuitive names for your
functions is important as well.

Functions should also be fairly short and to the point. Functions are best when they do one thing very
well. That one thing may **have** to be very complex sometimes, but the simpler your functions are the easier
they are to debug when things go wrong and things will go wrong. So some guidlines to take away from this
when writing your functions in the future are: Short, Simple, Do one thing, Named appropriately.

# Sources

[Python Functions](https://www.w3schools.com/python/python_functions.asp)

[What is a Function in Computer Programming](https://www.w3schools.com/python/python_functions.asp)

[Why Use Funtions](https://www.cs.utah.edu/~zachary/computing/lessons/uces-10/uces-10/node11.html)

[Scope](https://pythonspot.com/scope/)

[Nice R Code](https://nicercode.github.io/guides/functions/) Some good writing behind the philosophy of functions.

