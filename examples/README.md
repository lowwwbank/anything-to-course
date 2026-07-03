# Examples

## What's here

- **[`example-course/sql-for-analysts/`](example-course/sql-for-analysts/)** — a complete course produced by this skill, unedited. Input: a short topic brief ("teach SQL filtering and aggregation to analysts who know Excel but not SQL, ~4 hours total") plus a table schema. Every structural element the skill promises is in there — start with the [syllabus](example-course/sql-for-analysts/00-syllabus.md).
- **[`sample-lesson.md`](sample-lesson.md)** — a single standalone lesson excerpt from a different domain (product management), if you want the 2-minute version.

## What to look at in the example course

| Claim in the README | Where to see it |
|---|---|
| Learner attempts before the explanation | any lesson, the "Before reading on" block |
| Answers physically separate from tasks | tasks point to [`answers/`](example-course/sql-for-analysts/answers/) — nothing to peek at mid-lesson |
| Feedback explains the *cause*, demands a retry | [`answers/module-1.md`](example-course/sql-for-analysts/answers/module-1.md) |
| Exit tickets reach back to earlier lessons | end of [lesson 2.1](example-course/sql-for-analysts/modules/02-aggregation/01-group-by-having.md) |
| Checkpoint tasks don't name the method | [module 2 checkpoint](example-course/sql-for-analysts/modules/02-aggregation/99-checkpoint.md), task 3 |
| Spaced review plan with retrieval tasks | [`review-schedule.md`](example-course/sql-for-analysts/review-schedule.md) |
| Confidence calibration | every independent task ("rate your confidence first") |

## Reproduce it

With the skill installed, this is the kind of prompt that produced it:

> Turn this into a course: audience — data analysts comfortable with Excel, zero SQL; goal — filter and aggregate production tables on their own; time budget — about 4 hours plus reviews; material — our `orders` table schema below. [schema]
