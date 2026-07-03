# Answers & Feedback — Module 2

## D. Diagnostic

1. `WHERE status = 'paid' AND (country = 'DE' OR country = 'FR')` — parentheses mandatory the moment AND meets OR. If you skipped them: redo lesson 1.2's retry variation before starting this module; aggregation will hide this bug even better.
2. About 12 rows — one per country present in the data; each row = one country plus its average. If you said "one row": that's the overall-vs-per-group distinction this module builds.

## 2.1 — Independent task

```sql
SELECT country, AVG(amount) AS avg_paid
FROM orders
WHERE status = 'paid' AND coupon_code IS NULL
GROUP BY country
HAVING AVG(amount) > 80;
```

**Filter placement reasoning (the part that matters):** "paid" and "no coupon" describe *individual orders* → WHERE, so coupon-driven orders never pollute the averages. "Average above €80" describes a *group's aggregate* → HAVING.

**Likely errors, by cause:**
- Coupon filter in HAVING → not expressible (a group has many coupon values) or, worse, rewritten as a filter on aggregates that computes averages over the *wrong* rows first. Cause: filters remove rows *before* grouping or groups *after* — placing one at the wrong stage changes what enters every sum.
- `coupon_code = NULL` → module 1's silent-zero bug, now hidden inside plausible-looking averages. Nothing errors; every average is just computed over zero extra rows than intended... or all rows. This is why the module said aggregation *hides* filtering traps.
- `HAVING avg_paid > 80` → most databases don't know SELECT's nickname yet at HAVING time; repeat `AVG(amount)`.

**Retry variation:** "Total refunded amount per coupon, coupons with ≥10 refunded orders only, exclude no-coupon rows." Two aggregates in play — one displayed, one in HAVING.

## C. Cumulative checkpoint

1. a) FROM → WHERE → GROUP BY → HAVING → SELECT (→ ORDER BY, if used). b) WHERE drops rows before grouping; HAVING drops groups after. c) NULL comparisons are unknown, WHERE keeps only definite trues; verbs: `IS NULL` / `IS NOT NULL`.

2. a) **WHERE** (a list; signal: "orders … over €300" — row property). b) **Aggregation without GROUP BY** — `COUNT(DISTINCT customer_id)`; signal: "how many". c) **GROUP BY + HAVING** — and it needs *two* aggregates compared (refund count vs total count); signal: "countries where". d) **WHERE** on one id — a lookup, the simplest tool wins; reaching for GROUP BY here is overengineering.

3. ```sql
   SELECT coupon_code, COUNT(*) AS paid_uses, AVG(amount) AS avg_amount
   FROM orders
   WHERE status = 'paid'
     AND coupon_code IS NOT NULL
     AND (country = 'FR' OR country = 'ES')
   GROUP BY coupon_code
   HAVING COUNT(*) >= 30;
   ```
   The hidden module-1 trap: no-coupon rows are NULL — without `IS NOT NULL` they'd either form their own NULL group (polluting the report) or vanish confusingly, depending on the engine. Naming that trap was the actual test; the query is secondary.

4. `!= 'BLACKFRIDAY'` drops the NULL rows too — every order that used *no* coupon disappears from the counts, which the analyst certainly wanted kept. Missing rows: all no-coupon orders. Fix: `WHERE coupon_code IS NULL OR coupon_code != 'BLACKFRIDAY'`.

5. ```sql
   SELECT agent, AVG(minutes_to_close) AS avg_close
   FROM tickets
   WHERE priority = 'high' AND escalated_to IS NULL
   GROUP BY agent
   HAVING COUNT(*) >= 20 AND AVG(minutes_to_close) < 30;
   ```
   If this worked, the capability transferred: row-level filters (priority, the NULL-based "never escalated") in WHERE; group-level thresholds (volume, average) in HAVING — on a table you'd never seen. That, not `orders` trivia, was the course's goal.

**Retry rule:** wrong on 2 or 4 → redo lesson 1.2 exit ticket tomorrow (the NULL rule is not yet automatic). Wrong on 3 or 5 → invent one more per-group question about *your own* work data and solve it; check placement reasoning against 2.1.
