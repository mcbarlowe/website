---
title: "Using Travis CI and Codecov with your Python Project"
date: 2019-05-20T00:22:29-04:00
draft: true
---
### by Matthew Barlowe

I'm going to cover two important concepts when it comes to
coding: Continuous Integration and Code Coverage. Continuous Integration
is the act of merging everyones code into the main code repository several
times a day instead of doing it once a day or every few days.

There are pros and cons to this behavior which is beyond the scope of the
article, but I like Continuous Integration (CI) because it fits in with
my own coding philosophy. I like to commit often
 usually after every feature/function I create.
This is because if something breaks I don't want to have to go back
through lines and lines of code to figure out what is actually breaking
things.

The second part of CI is each merge automatically runs tests to
make sure the new code doesn't break the old code. Automating tests
is a great behavior because it means never forgetting to
run them.

Test brings us to our next main topic of this article which is code coverage.
The idea of code coverage concerns the tests that we run which each
integration of the code. Code coverage looks at the test you have
written and determines what percentage of the code base the tests
actually cover. The best is to have your tests cover one hundred
percent of your code but that's not always possible. Sometimes
certain functions take to long and can't always be implemented
in a test as tests are meant to be short as possible. Still though,
shooting for one hundred percent code coverage is always a good goal
strive for.

There are tons of platforms out there to implement CI and measure
code coverage for your projects. The two I will be discussing in
this article is [Travis CI](https://travis-ci.org) for continuous
integration and [Codecov](https://codecov.io) for code coverage.

This article will require you have a Github account so go grab one
if you do not already have one. And if you are unfamiliar with git,
make sure to read my other articles on [learning to use git]({{< relref "git/gitintro" >}})


# Setting up Travis-CI


