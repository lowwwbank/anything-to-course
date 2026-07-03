# Quality Gate: Rubrics, Checklist, Anti-Patterns

Run this file's checklist over the finished course before delivering. Every unchecked box
is a defect to fix, not a suggestion.

## Author checklist (per lesson)

### Goal
- [ ] The outcome describes an action by the learner (not "understands", "knows about").
- [ ] Situation and quality standard are specified.
- [ ] The final task of the lesson actually tests this outcome.

### Structure
- [ ] Prerequisites are identified and diagnosable.
- [ ] New concepts arrive in a manageable number (roughly ≤5 per lesson).
- [ ] The lesson builds exactly one coherent capability.
- [ ] Ordering follows dependencies, not the source material's chapter order.

### Explanation
- [ ] The core principle is stated explicitly, not left to be inferred.
- [ ] Terminology is consistent (one name per concept).
- [ ] Every term was checked against the *target novice's* vocabulary.
- [ ] Every new term is defined before its first substantive use.
- [ ] Abbreviations are expanded AND explained at first appearance.
- [ ] No definition relies on other unexplained terms.
- [ ] No hidden new jargon inside examples, diagrams, tasks, or feedback.
- [ ] Details that don't serve the outcome were cut.
- [ ] Visuals explain; they don't decorate.

### Examples
- [ ] At least one fully worked example, with the *why* of each step.
- [ ] The choice process is shown, not just the result.
- [ ] There is a contrasting example or counterexample.
- [ ] The transferable principle is stated after the examples.

### Practice
- [ ] There is a short attempt or prediction before the explanation.
- [ ] There is a retrieval attempt without hints.
- [ ] Support fades across the task sequence.
- [ ] There is an independent task.
- [ ] There is a task where the method is not named.
- [ ] There is a new variation or new context.
- [ ] Material from previous lessons appears (exit ticket).

### Feedback
- [ ] Answers physically cannot be seen before the attempt (separate answers/ file).
- [ ] Feedback explains the cause of the error.
- [ ] Plausible wrong alternatives are debriefed.
- [ ] The learner is directed to a corrected retry.

### Retention & transfer
- [ ] +1 day review scheduled.
- [ ] +7 day review scheduled.
- [ ] Cumulative practice exists a few modules later.
- [ ] A delayed transfer task exists.
- [ ] The learner compares confidence predictions with actual results somewhere.

### AI involvement (if the course uses an AI tutor)
- [ ] The AI receives the goal and the rubric.
- [ ] The AI is required to cite specific fragments of the learner's answer.
- [ ] The AI separates errors from defensible judgment calls.
- [ ] Key facts are checkable against a source.
- [ ] No decision depends on a single model run.

## Rubric for open cases

Open cases are graded on process quality, not on matching one model answer. Six
dimensions; describe 2–3 quality levels per dimension when embedding in a course.

1. **Problem framing** — symptoms separated from the underlying problem; user, context,
   and desired outcome identified; no conclusions beyond what the data supports.
2. **Use of information** — available facts used; facts separated from assumptions;
   missing data named; uncertainty acknowledged.
3. **Alternatives** — more than one option considered; compared on explicit criteria; the
   strongest counterargument is engaged, not ignored.
4. **Decision** — tied to the goal; constraints and trade-offs weighed; scale of response
   matches scale of problem; conditions that would change the decision are named.
5. **Verification** — a testable next step; success and failure signals defined;
   misinterpretation risks considered.
6. **Communication** — reasoning reconstructable; terminology consistent; concrete enough
   to act on; noise doesn't bury the logic.

## Anti-patterns — never ship a course containing these

- Long explanation blocks with no practice until the end of the course.
- A quiz immediately after the text as the *only* evidence of learning.
- Questions whose answers are visible in the phrasing or on the same screen.
- New terms used before being explained; abbreviations expanded but not explained.
- Recognition-only testing (all MCQ, no free recall).
- Solutions shown before the learner attempts.
- A single example with no generalization and no contrast.
- Dozens of identical tasks with the method known in advance.
- Difficulty from confusing wording rather than from the trained discrimination.
- Trap distractors that don't correspond to real mistakes.
- Feedback that is only a score, or only praise, with no next step.
- Open cases without criteria; AI grading without a rubric.
- Topic ordering copied from the source material instead of the dependency map.
- Rereading and highlighting suggested as the primary consolidation strategy.
- Review decisions based on felt familiarity instead of retrieval results.
- A course optimized for completion speed and satisfaction scores over delayed performance.

## The success criterion for the whole course

The course succeeded not when it was easy to finish, but when — weeks later — the learner
recalls the key ideas, recognizes application situations without the tool being named,
chooses between similar approaches, explains their own decisions, fixes errors after
feedback, transfers the principles to new constraints, and needs progressively fewer
hints.

> An attempt before the explanation prepares the ground. The explanation builds the first
> model. The example shows application. Self-explanation builds connections. Retrieval
> strengthens memory. Feedback repairs the model. Spacing preserves knowledge. Contrast
> teaches choosing. A new context turns knowledge into capability. Calibration teaches
> the learner to run their own learning.
