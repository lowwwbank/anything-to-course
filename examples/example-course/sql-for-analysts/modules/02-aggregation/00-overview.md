# Module 2 — Aggregation

## Outcome

Given a per-group business question ("revenue by country", "which coupons drive refunds"), you write `GROUP BY` queries with the right aggregate functions, filter groups with `HAVING`, and — when the question doesn't name a tool — decide between row-filtering and aggregation yourself.

## Why it matters

Module 1 produced lists; stakeholders want *numbers*. Nearly every metric in a dashboard is an aggregation over filtered rows. The classic failure is answering a per-group question with an overall number (or vice versa) — plausible, confident, wrong.

## Prerequisites

Module 1: WHERE with text/number/NULL conditions, AND/OR with parentheses. Quick check: if `WHERE coupon_code != 'X'` dropping NULL rows doesn't ring a bell, redo lesson 1.2 first — aggregation inherits every filtering trap and hides them better.

## Diagnostic — before starting (answers in [../../answers/module-2.md](../../answers/module-2.md), section D)

1. From memory (module 1): write a WHERE clause for "paid orders from Germany or France" that can't be misread.
2. Prediction: "average order amount by country" — how many result rows do you expect for a 12-country table, and what does each row mean?

## Lessons

1. [GROUP BY and HAVING](01-group-by-having.md) — per-group metrics and filtering groups.
2. [Cumulative checkpoint](99-checkpoint.md) — modules 1+2 interleaved, methods not named.
