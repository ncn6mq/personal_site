Managing the (Hidden) Cost of Complexity in High-Level Software

I often hear it said that high level languages such as Python/Ruby/Javascript and the respective frameworks
that build on those languages are somehow “simpler” or “easier to learn” than their lower level counterparts.
And for those of us who have spent much of our development time (or still do) dealing with pointer errors,
debugging memory leaks, writing stringy, verbose Make configuration, and so on, it’s easy to appreciate the
conveniences of many modern languages.

Of course, we often hear arguments thrown about in the thousands of holy wars waged on forums and discussion
boards about the costs in performance of these higher level languages. Yet the performance tradeoff is a
Faustian bargain that most of us willingly pay for the perceived productivity gain of not being forced to
work with all that fun stuff like manual memory management, heavy static compilation/linking, etc, etc.
Yet, I think there’s a larger cost than performance that isn’t considered nearly as much in most discussions
I see. That is, the cost of conceptual ownership of the code that we write, deploy, and ship every day.

I want to be clear: This isn't debate on whether high-level software is better or worse than


The Moral of the Story

Know thy environment
Be very specific and clear in logging and exception messages, especially when exporting a library
Be curious  -- take stuff apart
Documentation before tests
Tests before code


