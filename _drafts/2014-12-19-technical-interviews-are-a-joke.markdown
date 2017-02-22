---
layout: post
blog_title:  "Technical interviews are a joke and here's why"
redirect_from: "/2014/06/06/some-useful-lesser-known-features-of-the-ruby-rails-console.markdown/"
permalink: "blog/rails-console-tips"
date:   2014-10-06 03:41:52
categories: rails ruby
---

Yes, yes, I know this is a tired argument but I've heard so much being
written without anything being truly said that I wanted to throw my
proverbial hat into the ring. 

I'll cut straight to the point: the current culture and style of technical
interviews in this industry is complete joke. It's a problem that exists
at both megacorporations at startups alike, and it's something that
needs to change if we're to have any notion of true talent within
industry.

Here are a few funny "patterns" I've noticed in the tech hiring
process.

1. Jumping straight into technical questions without so much as glancing at my resume
   or any of the projects I've worked on.
2. Not accepting a solution that differed from the solution they
   expected to see (what made things worse is that they insisted their
solution was ~O(n^2) when in fact the problem was NP-hard.)
3. Similarly, expecting a keyword answer related to a specific
   technology without understanding the general problem domain. (As an
example, I was once asked a question about how to prevent state conflict
when multiple threads insert items into an ordered queue. I responded
that the queue would have to hold some sort of lock which is
acquired/realized by the thread which "owns" the queue as it is being
used. As I explained this, the interviewer impatiently interrupted me
saying "No, no, no... You've got it all wrong, the answer is to use
Java's `synchronized` keyword")
4. Asking specific questions related to a technology that had absolutely
   nothing to do with the position I was applying for (Similar example, I
once went through a ~45 minute interview where every question asked related
to CSS rules in defining a page layout. The position I was applying for was a data
engineering role.).
5. Asking a question that's been rehashed from a prior interview (which
   itself was likely rehashed from a previous interview, and so on). It got to the point where I wanted to create a Bingo card of interview questions: What's the question? You want me to reverse a string in Java? Bingo! You want me to implement `atoi` in C. No problem, ok cool but first, I gotta mark off this square on this 5x5 grid here in my pocket.

What's concerning is that issues like these seem to happen more often than not whic indicates problem has less to do with the actual technical interview questions than the
fact that this style of interview is given more precedence than
substantive and qualitative aspects of an interview, such as you know, actually
getting to know the candidate, their interests and background. In
reality, specific technical questions have their place, but should be
used as sparingly as possible and only when absolutely relevant to the
job at hand.

So how did things get this way? It's really not that complicated and can
likely be explained by a few simple reasons:

  1. Laziness (Why actually try to get to know a candidate when I can
     just ask this very generic and obscure cut-and-paste question I got
     from EPI? Even better it has a solution in the back of the book, so
I don't even need to figure it out myself!)
  2. Ego (How dare this person take my time away from working our team's
     latest milestone this sprint? Obviously, our team only consists of
the best and brightest so I'll show them with this absurdly
irrelevant, arcane, and impractical question of extracting precise solutions to a Soduku puzzle)
  3. Herd Mentality: "Well Google asks stupid-hard questions in
     their interviews and they're the best tech company as evidenced by
their stupid-hard interviews. If we want to be the next Google and
compete in this hiring rat race then we need to be asking stupid-hard questions too!"

Now, I should further qualify that I'm not saying all
technical interviews are worthless or of little merit. The problem is
that for many hiring processes, overly broad, vague, and irrelevant technical 
questions comprise most, if not all of the hiring process when in reality, 
they should only be used as absolurely sparingly as necessary and also only when
absolutely relevant to the job at hand.

I say this having been on both sides of the interview table many, many
times throughout my career, and throughout this process I've found some
 arise. 
