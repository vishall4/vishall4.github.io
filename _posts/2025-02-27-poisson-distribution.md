---
layout: post
title: "Poisson Is Just Binomial Taken to Infinity"
date: 2025-02-27
tags: [Mathematics, Statistics, PoissonDistribution, BinomialDistribution]
excerpt_text: "Poisson isn't some separate magical formula that fell from the sky. It's literally just the Binomial Distribution with n pushed to infinity."
---

So I kept pulling at the thread. Chi-squared → Gamma Function → and now Poisson Distribution.

And here's the thing nobody tells you upfront — Poisson isn't some separate magical formula that fell from the sky. It's literally just the Binomial Distribution with n pushed to infinity.

Let me walk you through how my head broke it down.

## Start with something familiar.

You're flipping a coin n times. What's the probability of getting exactly k heads? That's Binomial:

P(X = k) = C(n,k) · pᵏ · (1-p)ⁿ⁻ᵏ

Three pieces. C(n,k) is the number of ways to pick which k throws land heads. pᵏ is the probability of those k heads happening. (1-p)ⁿ⁻ᵏ is the probability that everything else is tails.

Simple. Now here's where it gets interesting.

## What happens when n → ∞?

Say on average 3 people enter a store per hour. What's the probability that exactly 5 people walk in? You don't have a fixed number of "trials" like coin flips. People just... show up. Continuously.

So what do you do? You chop that hour into n tiny slices. Each slice has a tiny probability p = λ/n of someone arriving. Now it looks like a binomial problem — n trials, probability p each. And you ask: what happens when n → ∞?

Each piece of the binomial formula transforms:

**C(n,k)** — when n is massive and k is small, n(n-1)(n-2)...(n-k+1) ≈ nᵏ. So C(n,k) ≈ nᵏ/k!

**pᵏ** = (λ/n)ᵏ = λᵏ/nᵏ

These two combine: nᵏ/k! · λᵏ/nᵏ = **λᵏ/k!**. The n's cancel perfectly. What's left isn't really a "count" of anything — it's the remnant of choosing k slots and assigning each a probability, after n washes out.

**(1 - λ/n)ⁿ⁻ᵏ → e⁻λ**. That's just Euler's number definition: (1 + x/n)ⁿ → eˣ as n → ∞. This piece is the probability that every other moment is empty. Nothing happens in the rest of the interval.

## Put it all together:

**λᵏ/k! · e⁻λ**

That's the Poisson PMF. Not a new invention. Just the binomial distribution taken to its continuous limit.

Every term has a job. λᵏ/k! handles the probability of picking exactly k arrival moments out of infinitely many infinitesimal slots where order doesn't matter. e⁻λ handles the probability that nothing happens the rest of the time.

No mystical "arrival rate" hand waving. No "just memorize this formula." It's the binomial — zoomed in infinitely.

I want to teach maths the way I wish someone would've taught me — like a story, not a formula sheet.
