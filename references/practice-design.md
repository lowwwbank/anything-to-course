# Practice & Assessment Design

How to design tasks, questions, feedback, and review schedules. The governing constraint:
**the practice format must match the capability being built** — and a check that's easier
than the capability proves nothing.

## Practice format matrix

| Capability | Primary format | NOT sufficient as a check |
|---|---|---|
| Recall a term or principle | Short answer from memory, no options | Recognizing the wording among obvious options |
| Explain a relationship | Self-explanation, causal question, draw the diagram | Paraphrasing the paragraph |
| Discriminate similar concepts | MCQ with strong, debriefed distractors | Choosing an answer with no analysis of alternatives |
| Execute a procedure | Task with progressively removed scaffolding | Explaining what the procedure is for |
| Compute a quantity | Calculation with intermediate steps + interpretation | Plugging numbers into a formula given in the prompt |
| Select the right tool | Mixed task set where the method is not named | Executing a method named in the prompt |
| Make a decision | Case with constraints and a rubric | Offering an opinion with no data or alternatives |
| Transfer knowledge | New context, changed surface features | Repeating the example with different numbers |
| Produce an artifact | Project with quality criteria and an iteration | Submitting a first draft with no feedback loop |

Bloom's taxonomy may be used *after* design as a diversity check on cognitive actions.
It does not replace this matrix and is not a mandatory ladder.

## Question design

### Recall before recognition

Preferred sequence for any knowledge item:

1. Formulate the answer from memory.
2. Rate confidence (sure / probably / guessing).
3. Only then see options (if the item has them).
4. Choose, and explain the choice.
5. Check the answer file; compare the confidence rating with the outcome.

The confidence step is not decoration — it trains calibration. Learners who never compare
prediction with result keep trusting the fluency illusion and under-review exactly the
material they're weakest on.

### Multiple choice done right

MCQs earn their place for: discriminating close concepts, diagnosing known misconceptions,
selecting a method from conditions, and fast cumulative practice. Rules:

- Wrong options reflect *real* mistakes learners make, not filler. A distractor nobody
  would pick tests nothing.
- After answering, the feedback explains why each strong distractor is wrong. Untreated,
  a plausible false statement gains familiarity and later feels true (Roediger & Marsh
  2005).
- No trick questions: difficulty must come from the discrimination being trained, not
  from ambiguous wording or hidden requirements.
- The answer must not be inferable from the question's grammar or length of options.

### Tasks that don't name the method

In real work, problems don't arrive labeled with the chapter title. A fixed share of
tasks (especially in checkpoints) presents only the situation:

> What is going on here? What tool fits? Why that one? What alternatives did you
> consider? What data would raise your confidence? What risk remains? How will you
> verify the result?

## Scaffolding and fading

Sequence for every new task type:

1. **Worked example** — full solution with reasoning made visible (why this method, what
   signal points to it, where the typical error lurks, how to sanity-check).
2. **Completion task** — partially solved; the learner finishes.
3. **Independent task** — no notes, criteria stated upfront.
4. **Far task** — new context, changed surface features, or an added constraint.

Fade faster for capable audiences: for experienced learners, extended hand-holding is not
just wasted time — it can depress learning (expertise reversal effect). When unsure,
provide support but make it skippable ("If you already know X, jump to the task").

## Feedback structure

Feedback lives in `answers/`, one file per lesson, so it cannot be seen before the
attempt. Every feedback item:

1. names what is correct in the typical attempt;
2. locates the likely error precisely (which step, which assumption);
3. explains the *cause* of the error, not just the correction;
4. links the correction back to the principle;
5. gives the next step (retry instructions or a variation);
6. skips secondary nitpicks — one main correction beats five minor ones;
7. addresses the work, never the learner's person or talent.

"Incorrect, the right answer is X" is a reveal, not feedback. The learner must be able to
see the difference between their reasoning and the correct reasoning.

Base cycle: attempt → diagnosis → explanation → correction → new variation.

## Spacing and interleaving

### Review schedule defaults

- Right after the lesson (exit ticket) → +1 day → +7 days → +21–30 days; add +2–3 months
  for anything the learner needs durably. Scale intervals to course length and stakes.
- Every review is retrieval: questions, tasks, free recall — never "reread the lesson".
- Strongest pattern for high-stakes material: **successive relearning** — within a
  session, practice items to a criterion (e.g., 3 correct recalls), then repeat to
  criterion in each of several spaced sessions.

### Interleaving rules

- First practice of a new task type: blocked (learn the procedure).
- Then: mixed with confusable neighbors (train the discrimination).
- Interleave *tasks and cases*, not the expository text.
- Expect the mixed set to feel harder and produce more errors during practice — say so to
  the learner explicitly, because the subjective struggle is otherwise read as failure.

## AI as coach

When the course will be studied with an AI assistant (grading open cases, generating
variations, running reviews), embed these instructions into the course materials:

The AI is good for: generating task variations, asking clarifying questions, comparing an
answer against the rubric, finding missing assumptions, offering counterarguments,
showing alternative solutions, fast formative feedback, and running the spaced review
schedule.

The AI must NOT, without verification: assign final grades on complex open cases; invent
facts or sources; present its own preference as the professional standard; judge
"correctness" without the stated context; replace the rubric with a general impression.

For any open-case grading, give the AI: (1) the task's goal, (2) context and constraints,
(3) the source materials, (4) the rubric, (5) examples of quality levels, (6) the
requirement to cite specific fragments of the learner's answer, (7) the requirement to
separate errors from defensible judgment calls. Treat AI feedback as a hypothesis to
check, not a verdict.
