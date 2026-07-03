# Lesson 1.2 — NULL and combined conditions: where filters go quietly wrong

**You will be able to:** filter correctly when a column can be empty (NULL) and when conditions combine with AND/OR — the two places where a query returns plausible wrong data instead of an error.

---

## A real incident

Your teammate ran this to find orders *without* a coupon, for a "full-price customers" campaign:

```sql
SELECT order_id FROM orders WHERE coupon_code != 'WELCOME10';
```

The list came back, the campaign went out — and every full-price customer was missing from it. No error, no warning.

**Before reading on** (1 minute, commit to a guess): the diagnostic asked what sits in `coupon_code` when no coupon was used. Combine that with this incident — what do you think went wrong?

---

## The principle

**NULL** — the database's marker for "no value here". It is not an empty string, not zero: it's the absence of an answer. And it has one rule that breaks Excel instincts:

> Any comparison with NULL is neither true nor false — it's *unknown*, and `WHERE` keeps only rows that are definitely true.

So `coupon_code != 'WELCOME10'` doesn't keep the NULL rows: "is unknown ≠ 'WELCOME10'?" is unknown, and unknown rows are dropped. The full-price customers vanished silently. NULL gets its own verbs:

```sql
WHERE coupon_code IS NULL       -- no coupon used
WHERE coupon_code IS NOT NULL   -- some coupon used
```

## Worked example

"Orders that used no coupon, or used any coupon other than WELCOME10":

```sql
SELECT order_id
FROM orders
WHERE coupon_code IS NULL OR coupon_code != 'WELCOME10';
```

- *Why two conditions?* NULL rows and "different coupon" rows fail the same business test ("not the WELCOME10 crowd") but need different SQL verbs — one comparison can't catch both.
- *Typical error:* writing `coupon_code = NULL`. It doesn't error in most databases — it just never matches anything. Silent zero rows.
- *Sanity check:* row counts of `IS NULL` + `= 'WELCOME10'` + `!= 'WELCOME10'` should sum to the whole table. If they don't, some rows are falling through a crack — almost always a NULL crack.

## Second trap: AND/OR precedence

> "Paid orders from Germany or France."

```sql
WHERE status = 'paid' AND country = 'DE' OR country = 'FR'   -- WRONG
```

SQL glues `AND` tighter than `OR`, so this means "(paid AND German) OR (French, any status)" — refunded French orders slip in. Parentheses say what you mean:

```sql
WHERE status = 'paid' AND (country = 'DE' OR country = 'FR');
```

Rule of thumb: the moment a `WHERE` mixes `AND` with `OR`, add parentheses — even when they're technically redundant. You're writing for the next reader (often you, in three weeks).

## Contrast

Excel's filter dropdown treats blank cells as just another value you can tick. SQL makes absence a first-class concept with its own logic. Same surface task — "filter out the blanks" — different mental model. That's why this lesson exists and the Excel refresher didn't cover it.

## Explain it yourself

1. Why does `!= 'WELCOME10'` drop NULL rows while `IS NULL` catches them — what's different about the two checks?
2. Remove the parentheses from the correct paid-DE-or-FR query. Which extra rows enter the result, and why exactly those?

## Finish this query (completion task)

"Cancelled or refunded orders from Italy that used a coupon":

```sql
SELECT order_id
FROM orders
WHERE (status = ______ OR status = ______)
  AND country = 'IT'
  AND coupon_code ______;
```

## On your own (notes closed)

The growth lead asks: "Which paid orders either used no coupon or are over €200? Spain only. Give me id, amount, coupon."

Write the query. Rate confidence (sure / probably / guessing), then check [answers/module-1.md](../../answers/module-1.md), section 1.2 — the answer file also shows the two most common wrong versions and what each returns.

*Success criteria: parentheses make the AND/OR meaning explicit; NULL handled with IS NULL; text quoted, numbers not.*

## Exit ticket

1. From memory: why is `coupon_code = NULL` a bug even though it runs without error?
2. From lesson 1.1: the database processes FROM → WHERE → SELECT. Where in that order does the NULL-dropping happen?
