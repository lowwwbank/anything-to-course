# Course Blueprint: Canonical Structures

Templates for the course, module, and lesson level. Follow these when writing; deviate
only with a stated reason (e.g., a 1-hour primer drops cumulative checkpoints).

## Course level

```
<course-name>/
├── 00-syllabus.md
├── modules/
│   ├── 01-<module>/
│   │   ├── 00-overview.md
│   │   ├── 01-<lesson>.md ... NN-<lesson>.md
│   │   └── 99-checkpoint.md
│   └── ...
├── answers/                # one file per lesson: feedback, explanations, worked keys
└── review-schedule.md
```

### 00-syllabus.md must contain

1. **Capabilities** — the 3–8 observable outcomes, phrased as "given X, you will be able
   to Y to standard Z".
2. **Who this is for / prerequisites** — what the learner should already know; a 5-minute
   self-check with answers so they can verify.
3. **Module map** — modules, their capabilities, and the dependency order.
4. **How to study this course** — explicit instructions to the learner:
   - attempt every task before opening the answer file;
   - write the answer down (or say it aloud) — deciding "I'd know it" doesn't count;
   - rate confidence before checking (sure / probably / guessing);
   - follow `review-schedule.md`; reviews are retrieval, not rereading;
   - errors are material — every wrong answer gets a retry after reading the feedback.

### review-schedule.md must contain

- A table: what to review, when (offsets from completing each module: +1 day, +7 days,
  +21–30 days), and how (specific retrieval tasks, not "reread module 2").
- Cumulative checkpoints every 2–3 modules with interleaved tasks from all prior modules.
- A final note that finishing the course doesn't end the schedule — the last review lands
  2–3 months out for anything the learner needs long-term.

## Module level (00-overview.md)

1. **Learning outcome** — what the learner will be able to do after this module.
2. **Practical payoff** — where and why this capability matters (one paragraph, concrete).
3. **Prerequisites** — terms and procedures assumed; which earlier module covers each.
4. **Diagnostic** — 3–5 short retrieval questions on prerequisites plus one prediction
   question about the new topic ("What do you think happens if...?"). Answered before the
   module; the answer file says which lessons to revisit if items failed. No grades.
5. **Module map** — lessons and how they build on each other.

## Lesson level — the canonical flow

Every lesson follows this sequence. The order is the point: attempt precedes explanation,
practice precedes answers, feedback precedes the retry.

1. **Hook: a real problem.** Open with a situation, question, or decision the lesson
   resolves — not with a definition.
2. **Learner attempt or prediction.** One short prompt: "Before reading on, write down
   how you would...". Feasible on prior knowledge; 1–3 minutes; explicitly low-stakes.
3. **The principle, stated plainly.** After the attempt, name the core idea in one or two
   sentences. Define every new term at first use (see First-use rule below).
4. **Worked example.** Show not only *what* was done but *why*: why this method, what
   signal in the problem points to it, what would have led to a different choice, where
   the typical mistake hides, how to sanity-check the result.
5. **Contrast.** At least one of: an analogous example from a different context; a
   contrasting case needing a different solution; a counterexample that looks similar but
   doesn't fit; or a question about which features are essential vs. incidental.
6. **Self-explanation prompts.** 2–4 directed questions: Why is this step justified?
   What principle does it rest on? What changes if we remove one condition? Why is the
   alternative weaker here? How would you check your own conclusion?
7. **Completion task.** A partially solved problem; the learner finishes it. The solved
   part models the approach, the open part forces generation.
8. **Independent task.** Solved without notes. Instructions and success criteria stated
   *before* the task, in the task text.
9. **Feedback — in `answers/`.** Never inline where eyes fall on it prematurely. See
   `practice-design.md` for the feedback structure.
10. **Retry or variation.** After feedback, a corrected attempt or a new variation of the
    same task type.
11. **Exit ticket.** 2–3 retrieval questions: at least one from this lesson, at least one
    from an earlier lesson or module.

### First-use rule (applies everywhere: prose, examples, tasks, feedback, diagrams)

A term the target learner doesn't know must not carry explanatory load before it's
defined. Template for first use:

> **Term** — what it is in plain words; the feature that distinguishes it from similar
> concepts; why it matters for the current task.

Example:

> **ARPU** — average revenue per user over a chosen period. It gauges how well the user
> base is monetized, but by itself says nothing about profitability.

Not sufficient: expanding an abbreviation without explaining the meaning; defining a new
term through other unexplained terms; exiling the definition to a distant glossary;
hoping context will make it obvious; using several names for one concept without linking
them; introducing a term for the first time inside a question whose answer depends on it.

If an example needs several new terms at once: pre-teach the minimal vocabulary in a
short block, split the example into stages, replace non-essential jargon with plain
words, and defer secondary terms until actually needed.

### Worked example anatomy (for step 4)

A complete instructional case contains: (1) goal, (2) context, (3) available data,
(4) constraints, (5) the solution, (6) the reasoning path, (7) rejected alternatives,
(8) the outcome, (9) limits of applicability, (10) the generalized principle. Not every
case needs all ten spelled out, but reasoning, rejected alternatives, and the principle
are never optional — a solution shown without them teaches imitation, not judgment.

### Concreteness fading

For abstract models, sequence representations: concrete instance → intermediate
representation (diagram, table, semi-formal notation) → abstract form. Stopping at the
concrete example welds the knowledge to its surface details; starting at the abstract
form gives the novice nothing to anchor it to.

## Checkpoint level (99-checkpoint.md, every module; cumulative every 2–3 modules)

1. Free recall of key ideas (no options given).
2. Discrimination items between look-alike concepts/methods (with debriefed distractors).
3. A procedural or computational task.
4. A closed case with a constrained solution space.
5. An open case with a rubric (see `quality-rubrics.md`).
6. An integration task where the method is NOT named.
7. A typical-errors review: common wrong answers with "why this is tempting and why it
   fails".

Cumulative checkpoints interleave tasks across modules in mixed order, because choosing
which tool applies is exactly what interleaving trains.
