# Lesson 1.1 — SELECT and WHERE: pulling exact rows

**You will be able to:** translate a business question into `SELECT columns FROM table WHERE condition`, and predict the row count before running it.

---

## A real request

Slack message from your finance lead:

> "Can you pull all German orders over €100? Just the order id, amount, and date. Need it in 10 minutes."

**Before reading on** (1–2 minutes, write it down): using only Excel words, describe the steps you'd take to produce this list from the `orders` sheet. Which columns? Which filters?

---

## The principle

A SQL query is your Excel filter written as a sentence with a fixed word order:

**`SELECT`** — which columns to show (your "hide the columns I don't need").
**`FROM`** — which table.
**`WHERE`** — which rows to keep (your filter dropdowns).

The database reads it in a different order than you write it: first it finds the table (`FROM`), then keeps matching rows (`WHERE`), then shows the columns you asked for (`SELECT`). Keeping that order in mind is what lets you predict results instead of hoping.

## Worked example

The finance request, reasoned step by step:

```sql
SELECT order_id, amount, created_at
FROM orders
WHERE country = 'DE' AND amount > 100;
```

- *Why `country = 'DE'` and not `country = DE`?* Text values always sit in single quotes; without them SQL looks for a column named `DE` and errors. Numbers (`100`) never take quotes — quote them and comparisons may go alphabetical.
- *Why `AND`?* The request says German **and** over €100 — both must hold for a row to survive. `OR` would return every German order plus every large order worldwide: thousands of rows instead of dozens. The row count is your first sanity check.
- *Why `>` and not `>=`?* "Over €100" excludes exactly 100.00. Worth one clarifying message to the requester — in real work the boundary is where silent disagreements live.
- *Sanity check before hitting run:* Germany is one of the bigger markets, orders over €100 are maybe a fifth of orders. Expect hundreds, not 3 and not 300,000. If you get 0 rows, the first suspect is the filter value (`'de'` vs `'DE'` — text comparison is case-sensitive in most databases).

## Contrast: a look-alike that needs a different tool

> "How **many** German orders over €100 do we have?"

Same filter — different ask. The finance lead wants one number, not a list. That's `SELECT COUNT(*)` — counting is *aggregation*, module 2's territory. The signal to watch for: "show me the rows" → `SELECT columns`; "how many / total / average" → aggregation. Same `WHERE` survives in both.

## Explain it yourself

1. Why does `WHERE amount > '100'` (quotes around 100) risk a wrong result rather than just an error?
2. The database applies `WHERE` before `SELECT`. Why does that mean you can filter on a column you don't display?

## Finish this query (completion task)

Marketing wants the customer ids and amounts of all **refunded** orders from **France**:

```sql
SELECT ______, ______
FROM orders
WHERE status = ______ AND ______ = 'FR';
```

## On your own (notes closed)

Support asks: "List the order id and status of every order from Spain with an amount of €500 or more — oldest first is fine, order doesn't matter."

Write the full query from scratch. Before checking: state your predicted row count logic in one sentence, and rate your confidence: sure / probably / guessing.

*Success criteria: correct three clauses in order; text value quoted; `>=` not `>`; you stated a row-count expectation.*

➡️ Then — and only then — open [answers/module-1.md](../../answers/module-1.md), section 1.1.

## Exit ticket

1. From memory: in what order does the database process `SELECT`, `FROM`, `WHERE`?
2. From the syllabus self-check: what does one row of `orders` represent — and why does that matter for predicting row counts?
