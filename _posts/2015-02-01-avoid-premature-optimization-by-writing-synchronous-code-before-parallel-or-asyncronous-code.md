---
layout: post
blog_title:  "Avoid premature optimization by writing synchronous code before parallel code"
title: "Blog"
redirect_from: "/2015/02/01/avoid-premature-optimization-by-writing-synchronous-code-before-parallel-code.markdown/"
permalink: "blog/avoid-premature-optimization"
date:   2015-02-01 10:09:31
categories: parallel concurrency node scala go clojure
---

Perhaps the most disruptive paradigm shifts in software over the last decade has been the shift in focus towards concurrent or asynchronous
program design. This has been evidenced by the recent growth of such frameworks and languages as Node.js, Go, Clojure, and Scala, and so on each having
 made their respective novel contributions towards solving the challenges of software must do many things at once and do them very quickly.


When viewed in light of the complexity and demanding user requirements for modern software it's easy to understand the need for concurrent design.
 A single HTTP request to a server can consist of dozens of database queries, cache lookups, API calls, all of which in many applications must collectively occur in less than 1/10th of a second.
 Under such circumstances the margin of error is thin--the last thing you want to be dealing with when releasing a new
app is to have a server that's grinding to a halt costing users and revenue because it can't do basic multitasking.


However, these benefits of asynchronous design don't come for free. Asynchronous software is considerably more
awkward to write, as it defies our natural understanding of problem solving. No longer does a program run in a
sequential, deterministic, ordered process of sequential steps. This is a big deal. Almost everything we've ever grown to understand
in the world, simple or complex, has relied on the assumptions of cause and effect and this has been especially true in the world of
software where the rules are especially strict.


So what's my point? When it comes to the process of actually *developing*
software, asynchronous code is more costly to write in terms of developer productivity and software reliability/testability.
In order to mitigate these costs, it's incumbent for you to change the way your mindset on problem solving. For instance, when working with
an async-focused framework like Node.js it's easy to fall into the trap of taking the API at face
value and always using the default asynchronous functions. Unless absolutely necessary, this is a mistake. As with any engineering
problem, always begin with the simplest solution that doesn't compromise design
requirements then layer on complexity only as it's absolutely required. In more concrete terms __this means writing linear/synchronous
code first whenever it's practical to do so then refactoring to an asynchronous paradigm once your synchronous code is stable.__


Begin by developing core specifications of what you're trying to do, mapping out sequential steps for that specification and then
 writing the relevant tests. *Only* once those tests are passing and the system is stable should you begin
layering additional complexity. There are a variety of reasons for this approach, chief among them being the importance of
of creating modular, well-abstracted software design guided by readable, conceptually visible code. This may seem trite and obvious,
but in practice it's much more powerful than it seems, and in reality it's much more rare amongst development teams than it ought to be.
The reason being that focusign on parallel and asynchronous software design (or any complex engineering design) obscures the underlying architecture
of the problem at hand.

By taking a simpler, linear approach first, you and those who work with you will be
more able to identify key abstractions that form the relationships between the problem you're trying to solve and concrete
modules, classes, functions, and so on which make that solution a reality. As a bonus, you'll also be less likely to
be surprised by more elusive and costly bugs that often occur later in the development cycle. If you're having a hard time
getting unit tests for synchronous code stable then you can be darn sure you'll have a hard time fulfilling the same requirements
with your fancy callback driven asynchronous code. If there's a nasty bug that was hard to find in a synchronous
algorithm you can be darn sure it will be hard to find in asynchronous code for the same reasons.

Simplifying the early development process as much as practically possible improves productivity and long-term stability. It's a win-win.



#### Additional resources and recommended reading:

- [Callback Hell: A guide to writing asynchronous javascript programs](http://callbackhell.com/)
- [Premature optimization is the root of all evil](http://c2.com/cgi/wiki?PrematureOptimization)
- [Seven concurrency models in seven weeks](https://pragprog.com/book/pb7con/seven-concurrency-models-in-seven-weeks)

<hr/>

## Comments

{% include comments.html %}
