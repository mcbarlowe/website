---
title: "Loops"
date: 2019-04-18T19:07:08-04:00
draft: false
---

# by Matthew Barlowe

Remember all these code snippets must be wrapped in a class method or a
`public static void main` to actually run. For the idea/philosophy
behind loops and how to use them go [here]({{< ref "/python/loops" >}})

# `for` loops

    for (initialization; termination; increment){
        statement(s);
    }

Real world example:

    //++ operator increments the value by one
    for (int i=1; i<11; i++) {
        System.out.println("Your number is: " + i);
    }

Infinite loop can be created this way:

    for ( ; ; ) {
        //put code here
    }

Can also loop over an array like in R/Python like this:

    int[] numbers = {1,4,5,2,6,3,6,7}
    for (int item : numbers) {
        System.out.println("Your number is: " + i);
    }

# `while` loops

    while (count < 11) {
        System.out.println("Your number is: " + count);
        count ++;
    }

# `do-while` loops

The main difference between `while` and `do-while` loops in java is that
`while` loops evaluate the condition for continuing at the beginning of the
loop, and `do-while` evaluates its condition at the end of the loop. This means
a `do-while` loop will run at least once as opposed to a `while` loop which
could never run depending on the condition. You also have to initialize the
variable before you write the loop unlike `while` loops where you can
initialize the variable in the loop declaration.

    int count = 1;
    do {
        System.out.println("Your number is: " + count);
        count ++;
    } while (count < 11);

# Source

[`while` and `do-while`Statments](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/while.html)

