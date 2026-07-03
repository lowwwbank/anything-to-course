# Cumulative Checkpoint — Modules 1 + 2 interleaved

Notes closed. Tasks mix filtering and aggregation **without telling you which is which** — deciding is the skill. Write, rate confidence, then check [answers/module-2.md](../../answers/module-2.md), section C.

## 1. Free recall

a) The six-step processing order, from memory.
b) WHERE vs HAVING in one sentence each.
c) The NULL comparison rule, and the two verbs that respect it.

## 2. Which tool? (don't write the query yet)

For each request, name the construct(s) and the one signal word that decided it:
a) "Orders from Japan over €300, newest ten are fine."
b) "How many distinct customers refunded something last month?"
c) "Countries where refunds exceed 5% of orders."
d) "Did order 88123 use a coupon?"

## 3. Method not named (write it)

> "I think our coupon program is losing money in small markets. Can you pull something that shows, per coupon, how many paid orders used it and their average amount — but only for coupons that show up in at least 30 paid orders? France and Spain only."

Write the full query. Then one sentence: which module-1 trap is hiding in this request, and how your query avoids it.

## 4. Predict, then explain

Without running:

```sql
SELECT country, COUNT(*) FROM orders
WHERE coupon_code != 'BLACKFRIDAY'
GROUP BY country;
```

The analyst wanted "orders per country, excluding Black Friday coupon orders". What's wrong with the counts, which rows are missing, and what's the fix?

## 5. Transfer — new surface, same principles

You get a new table: `tickets (ticket_id, agent, priority TEXT, minutes_to_close NUMERIC, escalated_to TEXT /* NULL if never escalated */)`. Support lead asks: "Which agents average under 30 minutes on high-priority tickets they closed without escalating — counting only agents with 20+ such tickets?"

Nothing about `orders` transfers except the principles. Write the query.

---

**After checking:** log calibration misses ("sure" but wrong) into your review list. This checkpoint reappears in week 3 with new variations — see [review-schedule.md](../../review-schedule.md).
