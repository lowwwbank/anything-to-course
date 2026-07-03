# Module 1 — Filtering Rows

## Outcome

Given a business question and the `orders` table, you write a `SELECT ... WHERE` query with correct text, number, and NULL conditions — and predict roughly how many rows it returns before running it.

## Why it matters

Almost every analyst request starts with "only the rows where…". Get the filter wrong and every number downstream — averages, totals, dashboards — is quietly wrong. The most expensive filtering mistakes don't error out; they return plausible-looking wrong data.

## Prerequisites

Excel-style filtering instincts (see the syllabus self-check). No SQL assumed.

## Diagnostic — answer before starting (no grade; answers in [../../answers/module-1.md](../../answers/module-1.md), section D)

1. From memory: what does one *row* of the `orders` table represent?
2. In Excel you'd filter `country = "DE"`. Guess: how might the same idea look in SQL?
3. Prediction: an order has no coupon. What do you think sits in its `coupon_code` field — an empty string, a zero, or something else?

Question 3 is the module's trap. If you guessed "something else", the module will tell you whether you were right — after you've seen the mechanism.

## Lessons

1. [SELECT and WHERE](01-select-and-where.md) — pulling exact rows.
2. [NULL and combined conditions](02-null-and-logic.md) — the traps: NULL, AND/OR precedence.
3. [Checkpoint](99-checkpoint.md) — mixed practice, methods not named.
