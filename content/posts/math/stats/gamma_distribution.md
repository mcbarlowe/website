+++
title = "The Gamma Distribution"
date = "2021-06-27T02:03:36-05:00"
author = "Matthew Barlowe"
authorTwitter = "matthew_barlowe" #do not include @
cover = ""
tags = ["math", "statistics"]
Keywords = ["math", "statistics", "distributions"]
description = "a look at the Gamma Distribution and its uses"
showFullContent = false
katex = true
markup =  "mmark"
draft = false
+++

# The Gamma Distribution

The Gamma Distribution is a very useful distribution used to model Poisson processes.
The Poisson distribution determines the probability of a number of
events in a given time span. The Gamma distribution gives the probability
of a given wait time until the $$n$$th event is observed in that process.

# Gamma Distribution Parameters

The Gamma Distribution can be defined by two different sets of two parameters.
It can have a shape parameter of $${k}$$ and a scale parameter of $$\theta$$ (theta) or a
shape parameter of $$\alpha$$ (alpha) and a rate parameter of $$\beta$$ (beta).
With either set of parameters $$\alpha={k}$$ and  $$\beta={1/\theta}$$.
$$\beta$$ is also equal to the $$\lambda$$ of the Poisson process we are trying
to model with the Gamma Distribution.
Gamma distribution parameters can only be positive real numbers, meaning you can
never have a parameter for a gamma distribution be negative.

# Moments of the Gamma Distribution

The mean or expected value of a Gamma distribution is defined like so:

$$\mathop{{}\mathbb{E}}{[X]} = {k}\theta = \frac{\alpha}{\beta}$$

$$\mathop{{}\mathbb{E}}{[X]}$$ is the symbolic way of saying the "Expected Value of X".
Meaning that on average if you randomly drew a number from this distribution with these
parameters the average value of the draws would equal this number.  If you have worked
with the Normal/Gaussian distribution you have seen this expressed as $$\mu$$.

The variance is defined thusly:

$$\mathop{{}\mathbb{V}}{[X]} = {k}\theta^{2} = \frac{\alpha}{\beta^{2}}$$

$$\mathop{{}\mathbb{V}}{[X]}$$ can also be displayed as $$\textnormal{Var}({X})$$ or $$\sigma^{2}$$ when
dealing with Normal/Gaussian distributions.


# Purposes of the Gamma Distribution

The Gamma Distribution is used to predict the wait time until a future event happens. More specifically until
the $${k}$$th event happens of a Poisson random variable. So if we wanted to model the time it takes
until the fifth time some event happens in a Poisson process the Gamma Distribution would be
our go-to distribution.  The Gamma Function models the wait time between Poisson distributed events.
Or another way to put it is the Gamma models the time spent in each state between events.

As Aerin Kim notes in her excellent piece on the Gamma Distribution (link below in the sources):

> Poisson, Exponential, and Gamma distribution model different aspects of the same process.
Poisson distribution is used to model the # of events in the future, Exponential distribution
is used to predict the wait time **until the very first event**, and Gamma distribution is
used to predict the wait time **until the $${k}$$th event**. (Kim)

So basically let's say that a catastrophic flood happens in your area once in a hundred years.
This would be our rate of occurrences, or $$\lambda$$, of the Poisson process. So if we wanted
to know how long we would have to wait to see five catastrophic floods we would use a Gamma
distribution with the parameters of $$\alpha = 5$$ and $$\theta = 1/\lambda$$.

$$\theta$$ is our average wait time between events in our unit of time or rate parameter, which in this case is
100 years. Since one divided by one is one that means our average wait time between floods
that occur once every 100 years is one unit of our time interval which in this case is 100 years.
If our rate of floods was 5 every 100 years then $$\theta$$ would be .20 or 20 years on average
between floods.

$$\alpha$$ is our number of times we want the event to occur in this case 5
because we want to calculate the probability of wait times before the area experiences 5
catastrophic floods. Using the formulas above the expected value of our wait time
would be 500 years ($$\alpha * \theta$$) with a variance of 500 years squared as well $$5\cdot1^{2}$$

But what if we want to calculate the probability of the wait time for 5 catastrophic floods being
100 years or less? To calculate this we would just plug our parameters into the Gamma CDF
(In this case the exact function is the Erlang CDF because the math is easier, but the Erlang is just
a special case of the Gamma where $$\alpha$$ is a positive integer) function. Here both $$\lambda$$
and $${t}$$ are equal to one since our rate ($$\lambda$$) is one and our interval of wait time ($${t}$$) is one.
Don't confuse this with the $$\lambda$$ of the Poisson process that is actually
$$\lambda={rate}\cdot{t}$$

$$\begin{aligned} {P(T\le1)}&={CDF(1)} \\ &={1 - P(\text{events}\lt5 \text{ in interval t})} \\ &=1 - \sum_{n=0}^{\alpha-1}\frac{(\lambda{t})^{n}\exp^{-\lambda{t}}}{{n}!} \\ &=1 - \sum_{n=0}^{4}\frac{(1)^{n}\exp^{-1}}{{n}!} \end{aligned}$$

Doing the math on that will give us the value of .003 or .3% probability of seeing 5 catastrophic floods
in the interval of 100 years. If we wanted the probability of 5 floods in say 300 years or less our formula would look like this:

$$1 - \sum_{n=0}^{4}\frac{(3)^{n}\exp^{-1}}{{n}!}$$

Which gives us a probability of roughly .18. But enough of doing this by hand lets see how to do it in
python. I'm going to use the `scipy` package which contains all sorts of probability distributions including
the gamma. The CDF function takes parameters of the wait time or interval, $$\alpha$$, and scale which is equal to
our $$\theta$$ parameter.

```
from scipy.stats import gamma

#probability we see 5 floods in one interval of time or less
#with scale parameter equal to 1
gamma.cdf(1, 5, scale=1)
0.003659846827343713

#probability we see 5 floods in three intervals of time or less
#with scale parameter equal to 1
gamma.cdf(3, 5, scale=1)
0.18473675547622787

#probability we see 1 flood in three intervals of time or less
#with scale parameter equal to 1
gamma.cdf(3, 1, scale=1)
0.950212931632136
```

If you want to dive deeper into using the gamma function to model wait times for Poisson processes
please read the links below as they go into much great detail on the gamma function and its uses.



# Sources

[Gamma Distribution -- Intuition, Derivation, and Examples](https://towardsdatascience.com/gamma-distribution-intuition-derivation-and-examples-55f407423840) by Aerin Kim

[Gamma Distribution Explained | What is Gamma Distribution](https://www.mygreatlearning.com/blog/gamma-distribution/) by Somak Sengupta

[UCLA AP Statistics Curriculum 2007 Gamma](http://wiki.stat.ucla.edu/socr/index.php/AP_Statistics_Curriculum_2007_Gamma)

[Poisson, Exponential, and Gamma distributions](http://sherrytowers.com/2016/01/23/poisson-and-exponential-distributions/) by Sherry Towers

[Seven Must-Know Statistical Distributions and Their Simulations for Data Science](https://towardsdatascience.com/seven-must-know-statistical-distributions-and-their-simulations-for-data-science-681c5ac41e32) by Zijing Zhu

[How to Model Time Between Events Using the Exponential, Gamma, and Poisson Distributions](https://medium.com/geekculture/how-to-model-time-between-events-using-the-exponential-gamma-and-poisson-distributions-4b058a357a55) by Federico Riveroll

[Introduction to STAT 414](https://online.stat.psu.edu/stat414/lesson/introduction-stat-414) Penn State Department of Statistics
