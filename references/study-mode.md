# Study Mode: Running a Course as the Tutor

How to run study sessions over a course this skill produced (or any structured
material). The same science that shaped course *writing* governs course *running* —
the difference is that here the agent enforces the learning behaviors in real time.

## What a session looks like (10–20 minutes)

1. **Pick what's due.** Read the course's `review-schedule.md` and the calibration log
   (below). Due reviews and calibration-flagged topics come first; new lessons only
   after due reviews are done — new material is more fun than reviews, which is exactly
   why reviews go first.
2. **Retrieve before anything else.** Open with 2–4 retrieval questions from due
   material. Ask, then WAIT for the learner's answer. Never open a session by
   summarizing "what we covered last time" — that's rereading with extra steps, and it
   robs the learner of the retrieval attempt that makes the session work.
3. **Confidence before checking.** After each answer, ask "sure / probably / guessing?"
   — then give feedback. The comparison of confidence with correctness is the
   calibration training; skipping it turns the session into a quiz.
4. **Feedback per the rules.** Follow `practice-design.md` § "Feedback structure": name
   what's right, locate the error, explain the *cause*, link to the principle, give a
   retry or variation. One main correction beats five nitpicks.
5. **Variations, not repeats.** When the learner retries, change surface features
   (names, numbers, context) so they solve the problem, not recall the answer. When
   they're solid, escalate: new context, method not named, added constraint.
6. **Close with the log.** End the session by updating the calibration log and telling
   the learner exactly when to come back and for what.

## The calibration log

Maintain `study-log.md` next to the course:

```markdown
| date | item | confidence | result | next review |
|------|------|-----------|--------|-------------|
| 2026-07-03 | NULL rule (1.2) | sure | wrong | tomorrow |
```

Rules: "sure + wrong" → the item returns tomorrow regardless of schedule, and its topic
leads the next session. "Guessing + right" is also a flag — fragile knowledge, schedule
it sooner. Two clean spaced successes → the item graduates to the next interval.

## Hard rules (the learner will push against these — hold the line kindly)

- **Never show the answer before an attempt**, even when asked. Offer a scoped hint
  instead ("which clause filters rows vs groups?"), then require the attempt. Explain
  why once: answers-before-attempts feel efficient and don't stick.
- **Never summarize instead of quizzing.** If the learner asks "just remind me how X
  works", respond with the smallest question that lets them reconstruct it, help only
  where reconstruction fails.
- **Reviews are non-negotiable, rereading isn't a review.** If the learner wants to
  "quickly reread module 1", convert it: "let's do 4 questions from module 1 instead —
  faster and it'll actually stick."
- **Open tasks get the rubric.** Grade open cases against the course's rubric (or
  `quality-rubrics.md` § open cases), citing specific fragments of the learner's answer.
  Separate errors from defensible judgment calls, and say which is which.
- **Session ends with a next step**, never with praise alone: what's due, when, and one
  sentence on what improved since the last session (evidence, not cheerleading).

## Starting mid-course or with someone else's material

If there's no review schedule or log (foreign course, raw notes), build the minimum
first: ask what the learner already studied, run a 5-question placement over it,
create `study-log.md` from the results, and propose a schedule. Don't run sessions
blind — without knowing what's due, every session drifts toward comfortable material.
