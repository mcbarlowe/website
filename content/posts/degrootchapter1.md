---
title: "Probability and Statistics: Chapter 1"
date: 2019-11-10T15:34:22-05:00
draft: false
---

Ok this is going to be a series of blog posts about detaling my notes and thoughts as
I work through DeGroot and *Schervish's Probability and Statistics 4th Edition.* This may be
useful to you it may not be but I generally find I learn things better if I write down
what I'm thinking about them so without further ado, let's begin!

# The History of Probability

So apparently people have been gambling forever. Balise Pascal and Pierre Fermat started the
mathematical theory of probability.

# Interpretations of Probability

Apparently nobody can agree on a single scientific interpretation of what the term *probability* means. I wonder what the probability of that happening is? But there seems to
be three main different interpretations of probablity.

1. Frequency Interpretaion of Probability

So the probability of a specific outcome of a process will be obtained is interpreted as
the relative frequency that outcome is obtained if the process were repeated a large number
of times under similar conditions. However there are some problems with this definition.
The main thing being that the ideas are rather vague. "Large number" has no defnitive
measurement of what the number should be to be considered large enough.

Secondly, its stating that the experiment should be repeated under similar conditions but
again the conditions are not precisely described. The situations can't be exactly identical
or else the results would always be the same. So the trials have to have some random features in them.

Thirdly a shortcoming of the frequency interpretation of probability is that it applies only to
a problem where there are a large number of similar repetitions of a similar problem. Some
examples are that frequency interpretation can't be used to determine the probability that a
friend will get married or that a research project will lead to the development of a new
treatment for a disease in a period of time.

2. Classical Interpretation of Probability

The classical interpretation of probability is based on the concept of equally likely outcomes
and the sums of the probabilities must equal 1. For example with a coin there are only two possible outcomes and if we assume that both outcomes are equally likely they have the same
probability and since the probabilities must equal one then their probabilities must be 1/2. To
generalize if the outcome of some process is one of *n* different outcomes and if those outcomes
are equally likely to occur then the probability of each outcome is 1/*n*.

There are two main flaws when attempting to define a formal definition of probability from this
interpretation. One the concept of equally likely outcomes is based on the concept of probability
we are try to define. Two possible outcomes that are equally likely is the same as two outcomes have the same probability.

Second no systematic method is given for assigning probabilities to outcomes were we don't assume
them all to be equally likely. Look back at the problem of determing the probability of a friend
getting married. No reasonable person would assume all outcomes of that situation to be equally likely so a different method would be needed to determine the probabilities of each outcome.

3. Subjective Interpretation of Probability

The subjective interpretation of probability is that the probability a person assigns to a
possible outcome of some process represents their own judgment of the likelihood that the
outcome will be obtained. If people's judgements of the relative likelihoods of various combinations of outcomes satisfy certain conditions of consistency then it can be shown that
their subjective probabilities of the different possible events can be uniquely determined.

The downfalls to this is that the idea that a person's judgements be free from contradictions
or biases does not seem humanly possible unless the person is willing to adopt a collection of
judgements known to be consistent. Also these subjective interpretations provide no objective
basis for two or more  people working together to reach a common evaluation of the state of
knowledge.

So the mathematical theory of probability can be done without regard to the controversies of
the different interpretations of the term probability.

# Experiments and Events

An experiment is any process, real or hypothetical, in which the possible outcomes can be
identified ahead of time. An event is a well defined set of possible outcomes of the experiment.
The probability of each event is the way of saying how likely it is that the outcome of the
experiment is in the event.

Once probabilities have been assigned to outcomes there is agreementthat the mathematical
theory of probability provides the appropriate methodology to further study probabilities.

# Set Theory

**Sample Space:** The collection of all possible outcomes of an experiment is called the sample
space of the experiment. This space can also be thought of as a set or colleciton of the
different possible outcomes. Each outcome is a *point* or *element* in the sample space and
events are *subsets* of the sample space.

For example with rolling a six sided dice the sample space is the six numbers on the dice.

> S = {1, 2, 3, 4, 5, 6}

One event we call *A* is an even number is rolled on the dice represented thusly *A* = {2, 4, 6}.
Another event is rolling a number greater than 2 then the subset of our sample space would
be *B* = {3, 4, 5, 6}

The collections of sets called events will have three conditions for the rest of the book.

1. Condition 1: The sample space *S* must be an event where *S* is the sample space of some
experiment.

**Containment:** it is said that a set *A is contained in* another set *B* if every element of
the set *A* also belongs to the set *B*. This is expressed by A ⊂ B which says A is a subset
of B. Also can say that B contains A and also write B ⊃ A. For events this means that if A
occurs then so does B.

**Theorem 1.4.1:** Let A, B, and C be events. then A ⊂ S. If A ⊂ B and B ⊂ A, then A=B. If A⊂B and B ⊂ C, then A ⊂ C.

**Theorem 1.4.3:** Let A be an event then ∅ ⊂ A.

**Countable/Uncountable:** An infinite set A is countable if there is a one to one
correspondence between the elements of A and the set of natural numbers {1, 2, 3, ...}. A set is uncountable if it is neither finite nor countable. If it is said
that a set has at most countably many elements then the set is either finite or countable.

Examples of countably infinite sets include the integers, even integers, odd integers,
the prime numbers, and any infinite sequence. these sets can be put in one to one
correspondence with the natural numbers. Every infinite sequence of distinct items
is a countable set as its indexing puts it in one to one correspondence with the natural numbers. Examples of uncountable sets are the real numbers, the positive
reals, numbers in the interval [0, 1], and the set of all ordered pairs of real
numbers.

## Operation of Set Theory

**Complement:** The complement of a set A is defined to be the set that contains all
elements of the sample space S that do not belong to A. In terms of events the
compliment event of A is the event that A does not occur.

**Condition 2:** If A is an event then the compliment of A is also an event.

If A is an event the the compliment of the compliment of A is A. The compleiment of the empty set is S the sample space and the compilment of the sample space is the empty set.

**Union of Two Sets:** If A and B are any two sets, the union of A and B is defined
to be the set containing all outcomes that belong to A alon, to B alone, or to both
A and B. The notation for the union of A and B is A ∪ B.

For all sets A and B,
A ∪ B = B ∪ A,
A ∪ A = A,
A ∪ Ac = S,
A ∪ ∅ = A,
A ∪ S = S.
Furthermore, if A ⊂ B, then A ∪ B = B.

**Union of Many Sets:** the union of n sets A₁, ..., An is defined to be the set that
contains all outcomes that bleong to at least one of these n sets.

In terms of events the union of a colleciton of events is the event that at least
one of the events in the collections occurs.

**Condition 3:** If A1, A2, . . . is a countable collection of events, then the union of all the events also an event.

