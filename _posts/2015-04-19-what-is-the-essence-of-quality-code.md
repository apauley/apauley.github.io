---
layout: post
title: "What is the Essence of Quality Code?"
description: "Almost everyone has an opinion on what makes good code good. Here are some of mine."
category:
- musings
- quality
tags: []
permalink: what-is-the-essence-of-quality-code
---

Are you a good programmer? How do you know?
The definition of "good code" is probably very subjective, but maybe it can be helpful to try and define some
  less-subjective criteria for discerning between good code (a.k.a "my code") and the terrible excuses for code
  I have to wade through every day (a.k.a "my code from the month before").

The primary criteria for code quality that I currently value amounts to:

  1. Correctness
  1. __Elegance and Simplicity__
  1. Reliability and Predictability
  1. Speed and Efficiency

## Correctness

The code we write should at the very least be working correctly.

This may be so obvious that it's hardly worth saying. I mean, what is the point of writing code
that is _not_ working? But looking at the number of times we inadvertantly introduce bugs in our
code I think it is worth making this implicit assumption explicit.

What can we do to measure and guarantee correct code?

Unit tests are a great tool, especially if we can write them as
[property checks](https://en.wikipedia.org/wiki/QuickCheck).
But in recent months I (like many others before me) have started asking
"[how can we move these runtime checks to compile time?](https://twitter.com/BendotK/status/505419912857518080)"

Type systems are fascinating.
I'm beginning to think that we can encode a fair number of the checks we
currently do at runtime (and check with unit tests) into the type system.

Some programmers stop after they get a feature working, as if "working code" is the only thing that matters.
Correct and working code is obviously important, but it is only the first step towards quality code.

> &ldquo;A program that produces incorrect results twice as fast is infinitely slower.&rdquo;
>
> &mdash; <cite>John Osterhout</cite>

> &ldquo;Correctness is clearly the prime quality. If a system does not do what it is supposed to do, then everything else about it matters little.&rdquo;
>
> &mdash; <cite>Bertrand Meyer</cite>

## Elegance and Simplicity

> &ldquo;Everything should be made as simple as possible, but no simpler.&rdquo;
>
> &mdash; <cite>Albert Einstein</cite>

Complexity is one of the biggest problems in software.
Complex code are sometimes engineered like a
[Rube Goldberg machine](https://en.wikipedia.org/wiki/Rube_Goldberg_machine).
It may work, and it may look impressive, but the simple unimpressive solution is superior in every way.

Simple code is easier to reason about, more secure, easier to
[refactor](https://en.wikipedia.org/wiki/Code_refactoring),
generally easier to [maintain](https://en.wikipedia.org/wiki/Maintainability)
and less likely to be buggy.

Elegance and simplicity is the aspect I value most,
because it seems that all other aspects of code quality require simplicity,
or is at least vastly improved by simple and elegant code.

> &ldquo;Fools ignore complexity. Pragmatists suffer it. Some can avoid it. Geniuses remove it.&rdquo;
>
> &mdash; <cite>Alan J Perlis, [Epigrams in Programming #58][epigrams]</cite>

How do we make our code simpler and more elegant?
Various books and articles
[have](http://shop.oreilly.com/product/9780596510046.do)
[been](http://www.amazon.com/Refactoring-Improving-Design-Existing-Code/dp/0201485672)
[written](http://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)
on the subject, but I'll mention a few topics that stand out for me.

 * [Don't repeat yourself](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) ([remove duplication](https://en.wikipedia.org/wiki/Duplicate_code)).
 * [Don't Mix Different Levels of Abstractions](http://www.principles-wiki.net/principles:single_level_of_abstraction)
 * [Reduce the Attack Surface](https://en.wikipedia.org/wiki/Attack_surface)

> &ldquo;Simplicity does not precede complexity, but follows it.&rdquo;
>
> &mdash; <cite>Alan J Perlis, [Epigrams in Programming #31][epigrams]</cite>

According to Kent Beck's [4 Rules of Simple Design](http://c2.com/cgi/wiki?XpSimplicityRules), simple code:

  1. Passes all the tests.
  2. Clearly expresses the intent.
  3. Contains no duplication, even in config.
  4. Minimizes all the moving parts (functions, objects etc).

Most of the quotes related to simplicity in software resonates well with me:

> &ldquo;There are two ways of constructing a software design:
> One way is to make it so simple that there are obviously no deficiencies and the other way is to make it so complicated that there are no obvious deficiencies.
> The first method is far more difficult.&rdquo;
>
> &mdash; <cite>C.A.R. Hoare, The 1980 ACM Turing Award Lecture</cite>

> &ldquo;Complexity kills. It sucks the life out of developers, it makes products difficult to plan, build and test, it introduces security challenges and it causes end-user and administrator frustration.&rdquo;
>
> &mdash; <cite>Ray Ozzie</cite>

> &ldquo;Beauty is more important in computing than anywhere else in technology because software is so complicated. Beauty is the ultimate defense against complexity.&rdquo;
>
> &mdash; <cite>David Gelernter</cite>

> &ldquo;Simplicity is the ultimate sophistication.&rdquo;
>
> &mdash; <cite>Leonardo da Vinci</cite>

## Reliability and Predictability

One of the reasons that I like [Functional Programming][fpintro] so much is that it stresses the decoupling of
[pure functions](https://en.wikipedia.org/wiki/Pure_function) from functions with
[side effects](https://en.wikipedia.org/wiki/Side_effect_%28computer_science%29).
Pure, [referentially transparent](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29)
functions are reliable and predictable. We should do our best to maximise the amount of pure code we write.

Another reason I like Functional Programming is that it allows me to write simpler code.
And some of the greatest minds agree that you need simplicity in order to get reliability:

> &ldquo;Simplicity is prerequisite for reliability.&rdquo;
>
> &mdash; <cite>Edsger W. Dijkstra</cite>

> &ldquo;The price of reliability is the pursuit of the utmost simplicity. It is a price which the very rich find most hard to pay.&rdquo;
>
> &mdash; <cite>C.A.R. Hoare</cite>

> &ldquo;The cheapest, fastest, and most reliable components are those that aren't there.&rdquo;
>
> &mdash; <cite>Gordon Bell</cite>

## Speed and Efficiency

Speed optimisation is listed last, because:

> &ldquo;Premature optimization is the root of all evil.&rdquo;
>
> &mdash; <cite>Donald Knuth</cite>

When is a speed optimisation premature?
This is probably another subjective point, but I prefer to only do optimisations on pieces of code that has been shown to be bottlenecks in the system, e.g. after doing load testing.

[fpintro]: http://www.slideshare.net/AndreasPauley/an-introduction-to-functional-programming-at-the-jozi-java-user-group
[epigrams]: http://www.cs.yale.edu/homes/perlis-alan/quotes.html
