# Module 1 Checkpoint — mixed practice

Notes closed. For each task, write the answer, rate confidence (sure / probably / guessing), then check [answers/module-1.md](../../answers/module-1.md), section C. Expect this to feel harder than the lessons — mixed practice always does; that's the point, not a problem.

## 1. Free recall (no options)

From memory, in your own words:
a) The three clauses of a basic query and the order the database processes them.
b) The one rule that makes NULL comparisons dangerous.

## 2. Spot the difference (discrimination)

Both queries aim at "German orders that used a coupon". One is right.

```sql
-- A
WHERE country = 'DE' AND coupon_code IS NOT NULL
-- B
WHERE country = 'DE' AND coupon_code != ''
```

Which, and what exactly does the other one return?

## 3. Method not named

> "Something's off in our refund numbers. Can you get me everything refunded in France or Germany above €150? And tell me how much I should trust the list."

No construct is named — decide what to write, write it, and add one sentence on the sanity check you'd run before sending the result.

## 4. Predict, then explain

Without running it: what does this return, and is that what the author probably wanted?

```sql
SELECT order_id FROM orders
WHERE status = 'refunded' OR status = 'cancelled' AND country = 'IT';
```

## 5. Fix the incident

A campaign query was supposed to catch *all* non-WELCOME10 orders but silently lost rows. Reconstruct the buggy WHERE clause from memory, then write the fixed one.

---

**After checking:** for every task where your confidence said "sure" but the answer was wrong — that's a calibration miss; put the topic on tomorrow's review list (see [review-schedule.md](../../review-schedule.md)). Then do the retry variations in the answer file.
