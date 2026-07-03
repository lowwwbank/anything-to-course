# Lesson 2.1 — Choosing a Primary Metric

> Excerpt from a course generated with `anything-to-course` from a product-management
> handbook. Shows the canonical lesson flow: attempt → principle → worked example →
> contrast → practice with fading support. Answers live in a separate file.

**You will be able to:** given a product description and a set of candidate metrics,
choose the primary metric, justify the choice, reject plausible alternatives, and name
one risk of misreading it.

---

## A real decision

Your team ships a meal-planning app. The dashboard shows: downloads, weekly active users,
average session length, number of meal plans created, and subscription revenue. The CEO
asks: *"Which single number tells us whether the product is working?"*

**Before reading on** (2 minutes, write it down): which metric would you pick, and what's
one argument against your own choice?

---

## The principle

**Primary metric** — the one number that best reflects the value users actually receive,
chosen so that moving it almost certainly means the product got better for users. It is
not the biggest number, and usually not revenue: revenue can grow while the product gets
worse (price hikes, dark patterns).

The test for a candidate: *"Can this number grow while users get less value?"* If yes,
it's a supporting metric, not the primary one.

## Worked example

Candidate: **downloads**. Can it grow while users get less value? Easily — a marketing
push inflates downloads regardless of product quality. Reject: it measures acquisition,
not delivered value. ❌

Candidate: **average session length**. Longer sessions could mean engagement — or
confusion while users hunt for features. The signal is ambiguous, so it fails the test. ❌

Candidate: **meal plans created per active user per week**. This is the core action the
product exists for. Hard to grow without users actually getting value. Sanity check: could
it be gamed? Auto-generated plans nobody cooks from would inflate it — so pair it with a
guardrail (plan-to-shopping-list conversion). ✅ Primary metric, with one named risk.

Notice the *shape* of the reasoning: we didn't ask "which number is most impressive" but
"which number is hardest to move without delivering value" — and we still named how even
the winner could lie to us.

## Contrast

Same test, different product: a **tax-filing app**. "Documents filed per user per week"
would be absurd — the job is done once a year. Value there is completion rate and error
rate, not frequency. The principle transfers; the metric doesn't. A metric is primary
relative to the product's core job, never in general.

## Explain it yourself

1. Why is revenue usually a supporting metric rather than the primary one?
2. What would have to be true about the meal app for session length to become a *good*
   signal?

## Finish this analysis (completion task)

A language-learning app's candidates: registrations, daily streak length, lessons
completed per active user per week, ad revenue. Registrations and ad revenue fail the
value test because ______. Between streak length and lessons completed, the stronger
primary metric is ______ because ______, and its gaming risk is ______.

## On your own (notes closed)

A car-sharing service tracks: app opens, registered drivers, completed rides per active
user per month, average ride rating, support tickets. Choose the primary metric. Justify
it, reject the two strongest alternatives, and name one way your chosen metric could
mislead the team.

*Success criteria: applied the value test explicitly; rejected alternatives with reasons,
not vibes; named a concrete gaming/misreading risk.*

➡️ When done — and only then — open `answers/module-2.md`, section 2.1. Rate your
confidence first: sure / probably / guessing.

## Exit ticket

1. From memory: what is the one-sentence test for a primary metric candidate?
2. From lesson 1.2: name the difference between an input metric and an output metric —
   and classify your chosen car-sharing metric as one of the two.
