+++
title = "The Gamma Distribution"
date = "2021-06-27T02:03:36-05:00"
author = "Matthew Barlowe"
authorTwitter = "matthew_barlowe" #do not include @
cover = ""
tags = ["math", "statistics"]
keywords = ["math", "statistics", "distributions"]
description = "a look at the Gamma Distribution and its uses"
showFullContent = false
katex = true
markup =  "mmark"
draft = true
+++

# The Gamma Distribution

The Gamma Distribution is a two parameter family of continuous probability distributions.
That means it relies on two variables to determine the shape of its probability distribution curve.

# Gamma Distribution Parameters

The Gamma Distribution can be defined by two different sets of two parameters.
It can have a shape parameter of $${k}$$ and a scale parameter of $$\theta$$ (theta) or a
shape parameter of $$\alpha$$ (alpha) and a rate parameter of $$\beta$$ (beta).
With either set of parameters $$\alpha={k}$$ and  $$\beta={1/\theta}$$.
Gamma distribution can only be positive real numbers, meaning you can never have a parameter
for a gamma distribution be negative.

# Moments of the Gamma Distribution

The mean or expected value of a Gamma distribution is defined like so:

$$\mathop{{}\mathbb{E}}{[X]} = {k}\theta = \alpha/\beta$$

$$\mathop{{}\mathbb{E}}{[X]}$$ is the symbolic way of saying the "Expected Value of X".
Meaning that on average if you randomly drew a number from this distribution with these
parameters the average value of the draws would equal this number.  If you have worked
with the Normal/Guassian distribution you have seen this expressed as $$\mu$$.

The variance is defined thusly:

$$\mathop{{}\mathbb{V}}{[X]} = {k}\theta^{2} = \alpha/\beta^{2}$$

$$\mathop{{}\mathbb{V}}{[X]}$$ can also be displayed as $$\textnormal{Var}({X})$$ or $$\sigma^{2}$$ when
dealing with Normal/Gaussian distributions.


# Purposes of the Gamma Distribution

The Gamma Distribution is used to predict the wait time until a future event happens. More specifically until
the $${k}$$th event happens of a Poisson random variable. So if we wanted to model the time it takes
until the fith time some event happens the Gamma Distribution would be our goto distribution.
The Gamma Function models the wait time between Poisson distributed events. Or another way to put
it is the Gamma models the time spent in each state between events.

The parameters of the Gamma re

To predict the wait time until future events. The exponential distribution predicts wait time until the first event while the gamma predicts the wait time until the $${k}$$th event.


Poisson, Exponential, and Gamma distribution model different aspects of the same process. Poisson distribution is used to model the # of events in the future, Exponential distribution is used to predict the wait time **until the very first event**, and Gamma distribution is used to predict the wait time **until the $${k}$$th event**.

Poisson - used to model the number of events in a fixed segment of time i.e. probability of x number of floods in a 100 year span

Exponential - is the average waiting time between events in the poisson distribution i.e. the average span of time between the floods
with average wait time being $$1/\lambda$$ where $$\lambda$$ is the number of events on average from the Poisson distribution in that span
of time. Exponential is special case of the Gamma where $$\alpha$$ or $${k}$$ is equal to 1. The probability distribution of the time
intervals between poisson events. If the number of occurences of something in a time interval is poissonically distributed then
the time interval between each occurence is exponentially distributed.

* Discrete analogue of the Gamma is the [Negative Binomial Distribution](https://en.wikipedia.org/wiki/Negative_binomial_distribution)
* Erlang distribution and chi-square distribution are also special cases of gamma distribution.

Have some code here that shows the relation between the distributions with graphs of them


# Sources

[Gamma Distribution -- Intution, Derivation, and Examples](https://towardsdatascience.com/gamma-distribution-intuition-derivation-and-examples-55f407423840) by Aerin Kim

[Gamma Distribution Explained | What is Gamma Distribution](https://www.mygreatlearning.com/blog/gamma-distribution/) by Somak Sengupta

[UCLA AP Statistics Curriculum 2007 Gamma](http://wiki.stat.ucla.edu/socr/index.php/AP_Statistics_Curriculum_2007_Gamma)

[Poisson, Exponential, and Gamma distributions](http://sherrytowers.com/2016/01/23/poisson-and-exponential-distributions/) by Sherry Towers

[Seven Must-Know Statistical Distributions and Their Simulations for Data Science](https://towardsdatascience.com/seven-must-know-statistical-distributions-and-their-simulations-for-data-science-681c5ac41e32) by Zijing Zhu

[How to Model Time Between Events Using the Exponential, Gamma, and Poisson Distributions](https://medium.com/geekculture/how-to-model-time-between-events-using-the-exponential-gamma-and-poisson-distributions-4b058a357a55) by Federico Riveroll
