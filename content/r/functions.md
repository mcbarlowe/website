---
title: "Functions"
date: 2019-04-18T17:19:29-04:00
draft: False
---

#by Matthew Barlowe

This is the syntax for making a function in R:

    function.name <- function(arg1, arg2, arg3=2) {
        variable = arg1 + arg2
        print(arg3)
        variable # the last line of the function is the return value in R
    }

In R you can also pass an `...` argument to a function indicating that the funciton
can take any number of name or unnamed arguments as well in the function
parameters. This is similar to Python's `*args` and `**kwargs` parameters in
funciton defining.

# Sources

[Nice R Code](https://nicercode.github.io/guides/functions/)
