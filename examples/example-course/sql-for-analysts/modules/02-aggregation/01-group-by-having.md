# Lesson 2.1 — GROUP BY and HAVING: from rows to answers

**You will be able to:** compute per-group metrics (`COUNT`, `SUM`, `AVG` with `GROUP BY`), filter the groups with `HAVING`, and say which filter belongs in `WHERE` vs `HAVING` and why.

---

## A real request

> "Which countries brought us more than €50k in paid revenue this quarter? Country and total, that's all I need."

**Before reading on** (2 minutes): in Excel you'd probably reach for a pivot table. Write down: what goes in rows, what gets summed, and where the two different "filters" in this request live. (Hint: one filters *orders*, one filters *countries*.)

---

## The principle

**`GROUP BY`** collapses rows into one row per group, and aggregate functions (**`COUNT`, `SUM`, `AVG`, `MIN`, `MAX`**) compute one number per group — SQL's pivot table.

The request above contains two filters of different *kinds*, and SQL gives each its own home:

- "paid" tests **individual rows** → **`WHERE`**, applied *before* grouping;
- "more than €50k total" tests a **group's aggregate** → **`HAVING`**, applied *after* grouping.

Processing order: `FROM → WHERE → GROUP BY → HAVING → SELECT`. Module 1's order, extended by two steps.

## Worked example

```sql
SELECT country, SUM(amount) AS revenue
FROM orders
WHERE status = 'paid'
GROUP BY country
HAVING SUM(amount) > 50000;
```

- *Why is `status = 'paid'` in WHERE, not HAVING?* It's a property of a single order. Filtering rows early also means the sums never include refunded noise — putting it in HAVING isn't even possible (a group doesn't have one status).
- *Why repeat `SUM(amount)` in HAVING?* HAVING runs before SELECT's nicknames (`AS revenue`) exist in most databases — so you name the aggregate again.
- *Typical error:* adding a column to SELECT that isn't in GROUP BY (like `order_id`). A group of 3,000 German orders has no single order id — the database errors, or worse (in some engines) picks one arbitrarily.
- *Sanity check:* result should have at most one row per country that has any paid orders, and every revenue figure > 50000. One row per group — if you see 40,000 rows, you didn't group.

## Contrast: the same words, the other tool

> "Show me the paid orders over €50k." — no grouping anywhere: that's module 1, `WHERE amount > 50000`, a *list*.
> "Which **countries** are over €50k **in total**?" — per-group total: `GROUP BY` + `HAVING`.

The signal is not the number; it's whether the threshold applies to **one row** or to a **group's total**. Requests never say "please use HAVING" — the phrase "per X" / "by X" / "which X-es" is your cue.

## Explain it yourself

1. A query has both `WHERE amount > 100` and `HAVING SUM(amount) > 10000`. Describe what each filter removes, in order.
2. Why does moving `status = 'paid'` from WHERE into HAVING (rewritten somehow) *change the revenue numbers* even for countries that pass both versions? (Think: what enters the sums.)

## Finish this query (completion task)

"How many orders used each coupon, counting only coupons with at least 50 uses? Skip no-coupon orders."

```sql
SELECT coupon_code, COUNT(*) AS uses
FROM orders
WHERE coupon_code ______
GROUP BY ______
HAVING ______;
```

## On your own (notes closed)

> "Average paid order amount by country, but only countries where that average is above €80, and skip orders that used any coupon — I want the organic baseline."

Write the full query. State which of the three filters went to WHERE and which to HAVING and why, then rate confidence (sure / probably / guessing). Check [answers/module-2.md](../../answers/module-2.md), section 2.1.

*Success criteria: coupon and status logic in WHERE (row-level, uses IS NULL correctly); average threshold in HAVING; grouped column matches SELECT.*

## Exit ticket

1. From memory: the full processing order, FROM to SELECT — six words.
2. From lesson 1.2: your GROUP BY query counts coupon uses. What does `COUNT(coupon_code)` do with NULL rows — and when would that silently change an answer?
3. From lesson 1.1: "list the rows" vs "how many" — which construct does each phrase point to?
