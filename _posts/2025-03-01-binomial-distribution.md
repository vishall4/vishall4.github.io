---
layout: post
title: "Binomial Distribution"
date: 2025-03-01
tags: [Mathematics, Probability, Statistics]
excerpt_text: "Most distributions in probability and statistics begin here. It's discrete, it's built from a coin toss, and everything else grows from it."
---

<style>
.bi-title-anim { text-align: center; margin: 0 0 2rem; }
.bi-title-text { font-family: 'Source Serif 4', Georgia, serif; font-size: 2.1rem; font-weight: 700; color: #242424; display: inline-flex; align-items: baseline; gap: 0; letter-spacing: -0.02em; line-height: 1.2; }
.bi-box-wrap { position: relative; display: inline-flex; align-items: baseline; cursor: pointer; }
.bi-text { display: inline-block; padding: 2px 6px; border: 2px solid #242424; border-radius: 4px; font-weight: 700; position: relative; z-index: 2; background: #fff; transition: border-color 0.3s, color 0.3s; }
.bi-box-wrap:hover .bi-text, .bi-box-wrap.open .bi-text { border-color: #534AB7; color: #534AB7; }
.bi-lid { position: absolute; top: -8px; left: 50%; transform: translateX(-50%) rotateX(0deg); transform-origin: bottom center; width: 52px; height: 10px; background: #242424; border-radius: 3px 3px 0 0; z-index: 3; transition: transform 0.4s cubic-bezier(0.34, 1.56, 0.64, 1), opacity 0.3s, background 0.3s; }
.bi-box-wrap:hover .bi-lid, .bi-box-wrap.open .bi-lid { transform: translateX(-50%) rotateX(-120deg) translateY(-12px); opacity: 0.3; background: #534AB7; }
.bi-people { position: absolute; top: -4px; left: 50%; transform: translateX(-50%) translateY(0px) scale(0); opacity: 0; font-size: 20px; white-space: nowrap; z-index: 1; transition: transform 0.5s cubic-bezier(0.34, 1.56, 0.64, 1) 0.15s, opacity 0.3s ease 0.15s; pointer-events: none; }
.bi-box-wrap:hover .bi-people, .bi-box-wrap.open .bi-people { transform: translateX(-50%) translateY(-32px) scale(1); opacity: 1; }
.bi-label { position: absolute; bottom: -22px; left: 50%; transform: translateX(-50%); font-family: -apple-system, BlinkMacSystemFont, sans-serif; font-size: 0.7rem; color: #6b6b6b; opacity: 0; transition: opacity 0.3s ease 0.25s; white-space: nowrap; }
.bi-box-wrap:hover .bi-label, .bi-box-wrap.open .bi-label { opacity: 1; }
</style>

<div class="bi-title-anim">
  <div class="bi-title-text">
    <span class="bi-box-wrap" id="biBox">
      <span class="bi-lid"></span>
      <span class="bi-text">Bi</span>
      <span class="bi-people">😊😊</span>
      <span class="bi-label">two outcomes</span>
    </span><span>nomial Distribution</span>
  </div>
</div>

<script>
var box = document.getElementById('biBox');
var opened = false;
box.addEventListener('click', function() {
  opened = !opened;
  if (opened) { box.classList.add('open'); } else { box.classList.remove('open'); }
});
setTimeout(function() {
  box.classList.add('open');
  setTimeout(function() { box.classList.remove('open'); }, 2000);
}, 800);
</script>

Most of the distributions you'll encounter in probability and statistics begin with the binomial distribution. It's a discrete distribution — and here's something worth keeping in mind: when you add up infinitely many discrete steps, you start approaching something continuous. That idea will matter later.

---

## A Coin Toss

You toss an unbiased coin. There are two sides — heads or tails — so either one appears.

Now the terminology: tossing a coin is called a **trial**. Unbiased coin means it isn't rigged. No magnets, no weighted sides, nothing influencing the outcome. There's a 50-50 chance of landing heads or tails.

Two sides of the coin — so only two things can happen: heads or tails. We label one as **success** and the other as **failure**. Which one gets which label doesn't matter — it's just naming. Let's say heads = success.

A single trial like this — one attempt, exactly two possible outcomes, with a fixed probability — is called a **Bernoulli trial**. Named after the mathematician Jacob Bernoulli, but the idea is just what we described. One toss, two outcomes, known probability.

---

## What Does "Binomial" Even Mean?

The word itself tells you. **Bi** means two. **Nomial** means terms. A binomial is something with two parts.

In algebra, a binomial expression looks like *a + b* or *3x − 5* — two terms.

In probability, the two "terms" are our two outcomes: **success and failure**. That's the entire reason it's called the binomial distribution. It models situations where only two things can happen.

---

## Toss It Again

Now I toss the coin a second time. The probability is still 50-50.

A third time. Still 50-50.

A fourth time. Still 50-50.

Why doesn't the probability change? Because each toss has no idea what happened before it. The coin doesn't remember. The third toss doesn't know the first two were heads. It doesn't care.

This is what **independent** means — the outcome of one trial has absolutely no effect on the outcome of another. Each trial lives in its own world. One way to think about it: independent means unconditional, unaffected, not influenced by anything that came before.

And in the real world, you can only toss a coin a limited number of times — you have limited coins, limited time, limited patience. So the number of trials is **fixed**. Let's call it **n**.

---

## Now Read the Textbook Definition

> *"The binomial distribution is a probability distribution that models the number of successes in a fixed number of independent trials, where each trial has only two possible outcomes."*

Read it again slowly. Every single word in that definition is something we just described with a coin:

- **"probability distribution"** — it tells us how likely each outcome is
- **"number of successes"** — how many heads did we get?
- **"fixed number"** — we decided how many times to toss (n)
- **"independent trials"** — each toss doesn't affect the next
- **"two possible outcomes"** — heads or tails, success or failure

This definition didn't come from nowhere. Someone watched a coin toss and wrote down what they saw. That's it.

Here's another way to see the structure:

A **binomial distribution** is a **probability distribution** where we have a **fixed number of independent trials**, and each independent trial has a **success and a failure**. The outcome — the thing our random variable X represents — is the count of successes.

---

## Before the Formula: What Is Probability?

We keep saying "probability" so let's be precise about what it actually means before writing any formulas.

**Probability is a number between 0 and 1 that measures how uncertain we are about something.**

That's it. It's a measure of uncertainty. Nothing more.

- When probability is close to **0** — the event is very unlikely. But it can still happen. A 1% chance is small, but it's not zero.
- When probability is close to **1** — the event is very likely. But it still might not happen. A 99% chance is almost certain, but it's not guaranteed.
- When probability is **exactly 0** — the event is impossible. It will never happen, under any circumstances.
- When probability is **exactly 1** — the event is certain. It will always happen, no matter what.

Here's the subtle part that's worth pausing on: probability measures *uncertainty*. At exactly 0 or exactly 1, there is no uncertainty left. Everything is fully determined. So in a sense, probability doesn't have a job at the extremes — there's nothing random left to measure.

For our unbiased coin, the probability of heads on any single toss is **p = 0.5**. The probability of tails (failure) is **1 − p = 0.5**.

We'll use **p** as a general symbol going forward. It doesn't have to be 0.5. A biased coin might have p = 0.7 for heads. A medical treatment might succeed with p = 0.85. A machine learning model might classify correctly with p = 0.92. The binomial distribution works for any fixed probability p between 0 and 1.

---

## Building the Formula From a Question

Here is the binomial probability formula:

**P(X = k) = C(n,k) · pᵏ · (1-p)ⁿ⁻ᵏ**

If you've never seen this before, it looks intimidating. So let's not start by staring at it. Let's start by asking a question, answering it step by step, and watching the formula build itself.

**Question: I toss a fair coin 4 times. What is the probability of getting exactly 1 head?**

### Step 1 — Where can that 1 head go?

If there's exactly 1 head in 4 tosses, the head could appear in the 1st, 2nd, 3rd, or 4th position:

- **H** T T T
- T **H** T T
- T T **H** T
- T T T **H**

That's **4 possible arrangements**. This is what the C(n,k) part of the formula calculates — it counts the number of ways to place k successes among n trials.

C(n,k) is read as "n choose k." For our example: C(4,1) = 4. Four ways to choose where the 1 head goes in 4 tosses.

The formula for n choose k is:

**C(n,k) = n! / (k! · (n-k)!)**

Where **n!** ("n factorial") means multiplying every whole number from 1 to n together: 4! = 4 × 3 × 2 × 1 = 24. The factorial counts how many ways you can arrange n things in a line. We divide by k! and (n−k)! to remove the duplicate arrangements — because in our case, we don't care about the order of the heads among themselves or the tails among themselves.

Let's verify: C(4,1) = 4! / (1! · 3!) = 24 / (1 × 6) = 4. Matches.

### Step 2 — What's the probability of one specific arrangement?

Take HTTT. What's the probability of this exact sequence?

- The H (head) has probability **p = 0.5**
- The first T (tail) has probability **1 − p = 0.5**
- The second T has probability **0.5**
- The third T has probability **0.5**

We **multiply** them together. Why? Because the tosses are independent. For independent events, the probability of all of them happening together is the product of their individual probabilities:

**P(A and B) = P(A) × P(B)**

This is one of the most fundamental rules in probability. If two events don't affect each other, you multiply. (If they do affect each other, you need conditional probability — but that's a different story.)

So the probability of HTTT:

0.5 × 0.5 × 0.5 × 0.5 = 0.5⁴ = 1/16

Now, we can separate this into the "success part" and the "failure part":

- **Success part**: the 1 head has probability p = 0.5 → that's pᵏ = 0.5¹
- **Failure part**: the 3 tails each have probability (1−p) = 0.5 → that's (1-p)ⁿ⁻ᵏ = 0.5³ = 0.125

One arrangement = pᵏ × (1-p)ⁿ⁻ᵏ = 0.5 × 0.125 = 1/16

### Step 3 — Put it all together

Every arrangement (HTTT, THTT, TTHT, TTTH) has the same probability: 1/16. And there are 4 arrangements.

P(X = 1) = 4 × 1/16 = 4/16 = 1/4 = 0.25

Now look at the formula again with fresh eyes:

**P(X = k) = C(n,k) × pᵏ × (1-p)ⁿ⁻ᵏ**

Three pieces, each doing exactly one job:
1. **Count** the arrangements
2. **Multiply** the probability of all successes
3. **Multiply** the probability of all failures

That's the entire formula. It counts and it multiplies. Nothing else.

---

## A Second Example to Lock It In

**What is the probability of exactly 3 heads in 5 tosses of a fair coin?**

- n = 5, k = 3, p = 0.5

**Arrangements:**

C(5,3) = 5! / (3! · 2!) = (5 × 4 × 3 × 2 × 1) / ((3 × 2 × 1)(2 × 1)) = 120 / (6 × 2) = 10

There are 10 ways to place 3 heads among 5 tosses. (HHHTT, HHTHT, HHTTH, HTHHT, HTHTH, HTTHH, THHHT, THHTH, THTHH, TTHHH — if you list them out, you'll count exactly 10.)

**Probability per arrangement:**

0.5³ × 0.5² = 0.125 × 0.25 = 0.03125

**Total:**

P(X = 3) = 10 × 0.03125 = 0.3125

There's a 31.25% chance of getting exactly 3 heads in 5 fair coin tosses.

---

## Every Symbol, Pinned Down

Let's make sure nothing is left as jargon. Here's every symbol in the formula and exactly what it represents:

- **X** — The random variable: "how many successes did we get?" In our example: number of heads.
- **n** — Total number of trials (fixed beforehand). In our example: 4 coin tosses.
- **k** — The specific number of successes we're asking about. In our example: 1 head.
- **p** — Probability of success on a single trial. In our example: 0.5.
- **1 − p** — Probability of failure on a single trial. In our example: 0.5.
- **C(n,k)** — Number of ways to arrange k successes in n trials. In our example: 4 ways.

When we say the random variable X follows a binomial distribution, we write:

**X ~ B(n, p)**

Which reads: "X is distributed as Binomial with n trials and probability p." The squiggly ~ just means "is distributed as." And B(n, p) tells you the distribution has two parameters — n and p — that fully determine its behaviour. Change either one, and the entire distribution changes.

---

## Mean and Variance

Two results that are worth knowing. If you toss a coin 100 times with p = 0.5:

**Mean (expected value)** — the average outcome you'd expect if you repeated the experiment many times:

μ = np = 100 × 0.5 = 50

You'd expect about 50 heads. That should feel obvious — and that's the point. The math confirms the intuition.

**Variance** — how much the outcome typically deviates from that average:

σ² = np(1-p) = 100 × 0.5 × 0.5 = 25

The standard deviation is σ = √25 = 5. So most of the time, you'll get somewhere between 45 and 55 heads. The variance tells you how spread out the results are around the mean.

Notice something important: the mean is **np** and the variance is **np(1−p)**. Since (1−p) is always less than or equal to 1, the variance is always **less than or equal to** the mean for a binomial distribution. Keep this fact in your back pocket — when we get to the Poisson distribution, we'll see something different happen: mean and variance become *equal*. That difference has real meaning.

---

## The MLE Connection

Here's something most textbooks mention in passing but don't explain well. It's worth pausing on because it shows up everywhere in machine learning.

The binomial formula is actually the foundation of **Maximum Likelihood Estimation (MLE)**. MLE is a method that asks: *"Given the data I observed, what value of the parameter p would make this observed data the most likely to occur?"*

Here's why this matters: because of how MLE works mathematically, the **average** of a binomial distribution always sits at the peak — the most probable outcome.

Think about it concretely. If you toss a fair coin 100 times, which number of heads is most probable?

- Exactly 50 → highest probability (the peak)
- 49 or 51 → very close, slightly lower
- 40 → noticeably less likely
- 10 → extremely unlikely
- 0 → essentially impossible

The peak of the binomial distribution sits at **np** — the mean. MLE is mathematically formalizing the same idea: the most likely parameter value is the one that places the peak at your observed data.

This isn't just a coin toss curiosity. In machine learning:
- **Logistic regression** models binary outcomes (success/failure) using the same probability p
- **A/B testing** compares two binomial distributions to determine which has a higher p
- **Neural networks** with sigmoid activation functions output a number between 0 and 1 — that's a success probability, exactly like our coin

---

## Bonus: Seeing Combinatorics in Poker

If you've understood everything above, here's a place where it all comes together beautifully — and if poker isn't your thing, feel free to skip this section entirely. The core concepts are already covered.

A standard deck has 52 cards (4 suits × 13 ranks). In poker, you're trying to make the best possible 5-card hand. How many total 5-card hands exist?

C(52,5) = 52! / (5! · 47!) = (52 × 51 × 50 × 49 × 48) / (5 × 4 × 3 × 2 × 1) = 311,875,200 / 120 = 2,598,960

That's the same C(n,k) we've been using. Same formula, same logic — count how many ways to choose k items from n, where order doesn't matter.

Now probability becomes a simple division. How likely is a Royal Flush? There are exactly 4 Royal Flushes (one per suit):

P(Royal Flush) = 4 / 2,598,960 ≈ 1 / 649,740

About 1 in 650,000. That's why the whole table goes silent when someone hits one — the rarity isn't a feeling, it's a mathematical fact.

How many 2-card starting hands are there in Texas Hold'em?

C(52,2) = (52 × 51) / 2 = 1,326

There are **6 ways** to be dealt pocket aces (choosing 2 aces from 4: C(4,2) = 6). But there are **16 ways** to hold Ace-King (4 choices for the Ace × 4 for the King). So when a player suspects their opponent has a strong hand, Ace-King is nearly three times more likely than pocket aces. Every decision at the table — call, raise, fold — is combinatorics and probability running underneath.

**Pot odds** connect this directly to decision-making. If you need one more card of your suit to complete a flush, and there are 9 remaining cards that complete it out of 47 unseen cards, your probability is 9/47 ≈ 19%. If the pot offers you better than 5:1 odds on your money, calling is mathematically profitable in the long run. Poker players call this "+EV" (positive expected value) — and it's the same expected value calculation that shows up in reinforcement learning and decision theory.

---

## What Comes Next

The binomial distribution handles situations where n is fixed and countable — 10 tosses, 50 patients, 200 survey responses.

But what happens when the "trials" aren't countable? What if someone could walk into a store at any moment — at 2:14 PM, at 2:14:33 PM, at 2:14:33.7291 PM? Time is continuous, so there's no natural n.

The answer: push n to infinity while keeping the average rate constant. The formula that falls out on the other side is the **Poisson distribution** — and it's built entirely on what we've covered here.

---

*Next: [Poisson Is Just Binomial Taken to Infinity](/poisson-distribution/)*
