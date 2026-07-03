# SQL for Analysts: Filtering & Aggregation

A ~4-hour self-study course (plus scheduled reviews) for analysts who know Excel but not SQL.

## What you will be able to do

1. **Pull the exact rows you need**: given a business question and a table, write a `SELECT ... WHERE` query with correct text, number, date, and NULL conditions — and predict how many rows it returns before running it.
2. **Turn rows into answers**: compute per-group metrics with `GROUP BY` and aggregate functions, filter groups with `HAVING`, and explain why a metric is per-group rather than overall.
3. **Choose the right tool unprompted**: given a question that doesn't say "use WHERE" or "use GROUP BY", decide which construct answers it and defend the choice.

## Who this is for / prerequisites

You can: filter a column in Excel, write a formula like `=SUMIF(...)`, explain what a table row is.
You don't need: any SQL, any programming.

**5-minute self-check** (answers in [answers/prerequisites.md](answers/prerequisites.md)):
1. In a spreadsheet of orders, how would you show only rows where country is "DE"?
2. What does `=AVERAGEIF(B:B, ">100")` compute, in your own words?
3. One order row contains: `1017, C-204, paid, 89.90, DE`. What might each field mean?

If any of these felt hard, spend 20 minutes with an Excel filtering refresher first — the course leans on these instincts.

## The table we use everywhere

```sql
orders (
  order_id     INT,          -- unique per order
  customer_id  TEXT,         -- e.g. 'C-204'
  status       TEXT,         -- 'paid' | 'refunded' | 'cancelled'
  amount       NUMERIC,      -- order total in EUR
  country      TEXT,         -- ISO code, e.g. 'DE'
  coupon_code  TEXT,         -- NULL when no coupon was used
  created_at   DATE
)
```

## Module map

| Module | Capability it builds | Depends on |
|---|---|---|
| [1. Filtering rows](modules/01-filtering-rows/00-overview.md) | capability 1 (exact rows, incl. NULL traps) | prerequisites |
| [2. Aggregation](modules/02-aggregation/00-overview.md) | capabilities 2 and 3 | module 1 |

## How to study this course (read this — it's not boilerplate)

- **Attempt every task before opening the answer file.** The struggle before the answer is where the learning happens; reading answers first turns practice into recognition, which decays in days.
- **Write your answer down** (or type the query) before checking. Deciding "yeah, I'd know it" doesn't count — that feeling is unreliable.
- **Rate your confidence** (sure / probably / guessing) before every check, then compare with the result. Mismatches are the most useful signal in the course — they show where your self-assessment is off.
- **Follow [review-schedule.md](review-schedule.md).** Reviews are short retrieval sessions, not rereading. Skipping them is how a finished course evaporates in three weeks.
- **Errors are material.** Every wrong answer gets one reread of the feedback and one retry. That loop is the course working, not you failing.
