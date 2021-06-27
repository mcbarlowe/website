---
title: "Loops"
date: 2019-04-17T20:51:38-04:00
draft: false
---

# by Matthew Barlowe

This is a tutorial going over the syntax of loops in R. If you want a break down
of how loops work and the philosophy please read my [Python loop tutorial]({{< ref "/python/loops.md" >}}).
Loops should be a last resort in R as they are slow and inefficient. Often you can do
what you need to in loops using the [`apply`](https://www.guru99.com/r-apply-sapply-tapply.html)
family of functions or the [`purrr`](https://purrr.tidyverse.org/) package.

# `for` loops

```R
for (i in 1:10) {
    print(paste("Your number is", i))
}

some_numbers <- c(1,3,5,3,0,10,35)

for (i in some_numbers) {
    print(paste("Your number is", i))
}
```

# `while` loops

```r
answer <- readline(prompt="What's the best part about Matt? ")
while (answer != 'He's Awesome") {
    print("Sorry, that isn't the correct answer.")
    answer <- readline(prompt='')
}
```

# `repeat` loops

These loops aren't present in Python. `repeat` loops are similar to `while` loops except
that `repeat` loops require the user to explicitly break the loop when the condition is met
instead of doing it automatically like `while` loops. Here is the example above
rewritten as a `repeat` loop.

```R
answer <- readline(prompt="What's the best part about Matt? ")
repeat {
    if(answer == "He's Aweseome"){
        break
    }
    print("Sorry, that isn't the correct answer.")
    answer <- readline(prompt='')
}
```

# Sources

[While vs. Repeat Loops in R](https://stackoverflow.com/questions/29215589/while-vs-repeat-loops-in-r)

I hate linking to this because it's Datacamp but it's free so hopefully they aren't making money off it

[Tutorial on Loops in R](https://www.datacamp.com/community/tutorials/tutorial-on-loops-in-r)




