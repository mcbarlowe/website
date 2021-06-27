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

* Two parameter family of continuous probability distributions. Exponential distribution, erlang distribution, and chi-square distribution are special cases of gamma distribution.
* Can have a shape parameter of $${k}$$ and a scale parameter of $$\theta$$
* or can have a shape paramter of $$\alpha={k}$$ with an inverse scale parameter of $$\beta={1/\theta}$$
* with either parameterization both parameters are positive real numbers
* discrete analogue of the Gamma is the [Negative Binomial Distribution](https://en.wikipedia.org/wiki/Negative_binomial_distribution)

The gamma distribution is the maximum entropy probability distribution for a random variable $${X}$$ for which:

$$\mathop{{}\mathbb{E}}{[X]} = {k}\theta = \alpha/\beta$$

is fixed and greater than zero and

$$\mathop{{}\mathbb{E}}[\ln(X)] = \psi({k})+ \ln(\theta) = \psi(\alpha) - \ln(\beta)$$

is fixed. $$\psi$$ is the digamma function.


# Purposes of the Gamma Distribution

To predict the wait time until future events. The exponential distribution predicts wait time until the first event while the gamma predicts the wait time until the $${k}$$th event.


Poisson, Exponential, and Gamma distribution model different aspects of the same process. Poisson distribution is used to model the # of events in the future, Exponential distribution is used to predict the wait time **until the very first event**, and Gamma distribution is used to predict the wait time **until the $${k}$$th event**.


# Sources

[Gamma Distribution -- Intution, Derivation, and Examples](https://towardsdatascience.com/gamma-distribution-intuition-derivation-and-examples-55f407423840) by Aerin Kim
