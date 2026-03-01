---
layout: post
title: "Gamma Function in One Page — No Horror"
date: 2025-02-24
tags: [Mathematics, GammaFunction, ChiSquared]
excerpt_text: "The chi-squared distribution is a special case of the gamma distribution. So I had to study the gamma function first. Every resource made it terrifying."
---

My earlier post mentions I was re-visiting chi-squared for experimental and pedagogical purposes so I started going through Wikipedia for the same, and I stumbled across one thing — THE CHI-SQUARED DISTRIBUTION IS A SPECIAL CASE OF THE GAMMA DISTRIBUTION. So I had to needed to study the Gamma Function first and I had to ask what is GAMMA FUNCTION? I looked through entire internet (only exaggeration obviously) and every resource I looked at made it seem like some rocket science stuff that could launch me into space, I mean Integral definitions thrown at you out of nowhere. Proofs that assume you already know what's going on. Formulas first, intuition never.

So I sat down and broke it apart myself. And honestly? It fits on one page (although requires some background of calculus).

Here's where my head went:

Factorial is simple. 5! = 5 × 4 × 3 × 2 × 1. Easy. But what's (3/2)!? Factorial is only defined for integers — so how do you extend it to everything else?

If you plot the known factorial values as dots on a graph, you could draw infinitely many curves through them. Some smooth, some wildly oscillating — all passing through the exact same points. So "connecting the dots" isn't enough. You need a constraint to pin down a unique curve (log convexity).

## That's where the Gamma Function comes in.

But instead of starting with the integral formula like every textbook does, I asked — what property do we actually NEED?

Factorial has a recursion: n! = n × (n-1)!. So whatever function we build, it needs to satisfy f(x) = x · f(x-1). Not just for integers. For everything. I started there, used integration by parts, and the integral just... reproduces the recursion. Then I checked the base case. It works. The whole thing holds together.

*(See my handwritten notes attached for the full proof — two pages, two approaches.)*

## The index shift

One thing I caught after — what I was technically proving is Γ(x+1) = x·Γ(x), not Γ(x) = x·Γ(x-1). There's an index shift between the two. Same idea, just shifted by one. Worth knowing so it doesn't trip you up when you see it written differently elsewhere.

The point is — I didn't start from the formula. I started from what the function needs to do, then showed the integral does it, then checked the base case. That's the natural direction. Not "here's a scary integral, now memorize properties."

**Gamma Function in one page. Two ways to see it. No horror.**

I want to teach maths the way I wish someone would've taught me — like a story, not a formula sheet.
