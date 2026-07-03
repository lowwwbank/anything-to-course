# Answers — Prerequisite Self-Check

1. **Filter country = "DE":** any answer describing Excel's column filter (dropdown on the country column → tick DE) works. The SQL equivalent you'll learn: `WHERE country = 'DE'`.
2. **`=AVERAGEIF(B:B, ">100")`:** the average of column B values that are greater than 100 — a *conditional* average. SQL splits the same idea into a filter (WHERE) plus an aggregate (AVG); module 2 connects them.
3. **The row:** one order: its id (1017), the customer who placed it (C-204), its payment status (paid), the total (€89.90), the country (DE). Knowing what one row *means* is what lets you predict how many rows a filter should return — the course leans on that habit constantly.

Comfortable with all three → start [module 1](../modules/01-filtering-rows/00-overview.md).
