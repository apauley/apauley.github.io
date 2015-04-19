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

The definition of "good code" is probably very subjective, but maybe it can be helpful to try and define some less-subjective criteria for discerning between good code (a.k.a "my code") and the terrible excuses for code I have to wade through every day (a.k.a "my code from the month before").

Here are some of the criteria for code quality that I value.

## Correctness

The code we write should at the very least be working correctly.
Some programmers stop after this step, as if "working code" is the only thing that matters.

Correct code is obviously important, but it is only the first step.

How do we measure and guarantee correct code?
Sure, unit tests are a great tool, especially if I can write them as property checks.
But in recent months I have started asking myself "how can I move these runtime checks to compile time?"
Type systems are fascinating, I'm beginning to think that I can encode a lot of the checks I'm currently running as unit tests into the type system.

> &ldquo;A program that produces incorrect results twice as fast is infinitely slower.&rdquo;
>
> &mdash; <cite>John Osterhout</cite>

> &ldquo;Correctness is clearly the prime quality. If a system does not do what it is supposed to do, then everything else about it matters little.&rdquo;
>
> &mdash; <cite>Bertrand Meyer</cite>

## Elegance and Simplicity

Complexity is one of the biggest problems in software.
Simple and elegant code don't just work, it works in a clear and concise way.

Complex code are sometimes engineered like a [Rube Goldberg machine](https://en.wikipedia.org/wiki/Rube_Goldberg_machine).
It may work, and it may look impressive, but the simple unimpressive solution is superior in every way.

Simple code is easier to reason about, easier to refactor and less likely to be buggy.

> &ldquo;There are two ways of constructing a software design:
> One way is to make it so simple that there are obviously no deficiencies and the other way is to make it so complicated that there are no obvious deficiencies.
> The first method is far more difficult.&rdquo;
>
> &mdash; <cite>C.A.R. Hoare, The 1980 ACM Turing Award Lecture</cite>

> &ldquo;Beauty is more important in computing than anywhere else in technology because software is so complicated. Beauty is the ultimate defense against complexity.&rdquo;
>
> &mdash; <cite>David Gelernter</cite>

> &ldquo;Complexity kills. It sucks the life out of developers, it makes products difficult to plan, build and test, it introduces security challenges and it causes end-user and administrator frustration.&rdquo;
>
> &mdash; <cite>Ray Ozzie</cite>

> &ldquo;Simplicity is the ultimate sophistication.&rdquo;
>
> &mdash; <cite>Leonardo da Vinci</cite>

## Reliability and Predictability

One of the reasons that I like Functional Programming so much is that it stresses the decoupling of pure functions from functions with side effects.
Pure, referentially transparent functions are reliable and predictable. We should do our best to maximise the amount of pure code we write.

Another reason I like Functional Programming is that it allows me to write simpler code.
And some of the greatest minds agree that you need simplicity in order to get reliability:

> &ldquo;The price of reliability is the pursuit of the utmost simplicity. It is a price which the very rich find most hard to pay.&rdquo;
>
> &mdash; <cite>C.A.R. Hoare</cite>

> &ldquo;Simplicity is prerequisite for reliability.&rdquo;
>
> &mdash; <cite>Edsger W. Dijkstra</cite>

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
