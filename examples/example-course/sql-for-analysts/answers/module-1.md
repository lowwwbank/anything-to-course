# Answers & Feedback — Module 1

Read the feedback for your attempt, find the *cause* line, then do the retry. Comparing your reasoning with the correct reasoning is the learning step — don't skip to the code.

## D. Diagnostic

1. One row = one order (id, customer, status, amount, country, coupon, date).
2. Any guess resembling `WHERE country = 'DE'` is great; "some kind of filter condition" is fine too — the diagnostic activates, it doesn't grade.
3. **Something else** — a special marker called NULL. If you guessed empty string or zero: that's the Excel instinct this module retrains, and lesson 1.2 shows why it matters. Nothing to fix yet; just notice the prediction gap.

## 1.1 — Independent task

```sql
SELECT order_id, status
FROM orders
WHERE country = 'ES' AND amount >= 500;
```

**What's usually right:** clause order, quoting `'ES'`.

**Likely errors, by cause:**
- `> 500` instead of `>=` → the request says "€500 **or more**"; `>` silently drops exactly-500 orders. Cause: boundary words ("or more", "over", "at least") map to different operators — reread the request for the boundary word before choosing.
- `'500'` in quotes → in some databases this compares text alphabetically ("'500' > '1000'" is *true* as text!). Cause: quoting decides the comparison type, not just syntax. Numbers stay bare.
- `country = ES` unquoted → error: SQL hunts for a column named ES. Text values always quoted.

**Row-count expectation:** something like "Spain is a mid-size market, ≥€500 is rare — expect dozens, not thousands." Any explicit expectation counts; having none is the miss.

**Retry variation** (do it now, it's 60 seconds): same request for Portugal, "strictly under €25", show id and amount.

## 1.2 — Independent task

```sql
SELECT order_id, amount, coupon_code
FROM orders
WHERE country = 'ES'
  AND status = 'paid'
  AND (coupon_code IS NULL OR amount > 200);
```

**The two common wrong versions and what they actually return:**
1. `... AND coupon_code IS NULL OR amount > 200` (no parentheses) → AND binds tighter, so this is "(Spanish paid no-coupon) OR (*any* order anywhere over €200)". Refunded German orders at €300 walk right in. Cause: mixed AND/OR without parentheses never means what the sentence meant.
2. `coupon_code = NULL` → runs, matches nothing, the no-coupon half of the result silently disappears. Cause: NULL isn't a value you can `=`; comparisons with it are unknown, and WHERE drops unknowns. The verb is `IS NULL`.

**Retry variation:** "Paid German orders that used a coupon AND are under €50, or any German order over €500." Parentheses will carry all the meaning — write it so a colleague can't misread it.

## C. Checkpoint

1. a) SELECT / FROM / WHERE, processed FROM → WHERE → SELECT. b) Comparisons with NULL are neither true nor false — unknown — and WHERE keeps only definite trues, so NULL rows silently vanish from both `=` and `!=` filters.

2. **A is right.** B (`!= ''`) tests against an *empty string* — but no-coupon rows hold NULL, not `''`, and `NULL != ''` is unknown → dropped. B returns only rows that used a coupon, minus nothing — i.e., the same as `IS NOT NULL` *only if* the table never stores `''`. You can't know that from the schema, which is why the NULL verbs exist. If you picked B because "empty means empty string" — that's the Excel-blank instinct again; in SQL absence is NULL until proven otherwise.

3. ```sql
   SELECT order_id, amount, country, created_at
   FROM orders
   WHERE status = 'refunded'
     AND (country = 'FR' OR country = 'DE')
     AND amount > 150;
   ```
   Trust sentence should mention a *sanity check*, e.g.: "I'd sum the row count against the refunds dashboard for the same period — if the dashboard shows 3× more, my filter is too tight (or theirs counts cancellations)." The habit being tested: never send unverified filtered data during an incident.

4. AND binds before OR → "refunded (anywhere) OR (cancelled AND Italian)". The author almost surely wanted "(refunded OR cancelled) AND Italian". Extra rows: every refunded order outside Italy.

5. Buggy: `WHERE coupon_code != 'WELCOME10'` — drops the NULL (no-coupon) rows. Fixed: `WHERE coupon_code IS NULL OR coupon_code != 'WELCOME10'`.

**Retry rule:** any task wrong twice → redo its lesson's completion task tomorrow, then this checkpoint task again with the review-schedule swaps.
