# Learner Profile & Study Progress Specification

The framework maintains learner state in **two living documents** that serve different roles. This file specs both, and the boundary rule that decides which goes where.

| File | Location | Scope | Created |
|---|---|---|---|
| `learner-profile.md` | Learning home root | The learner as a person — identity, learning style, general traits — plus an index of all studies | Phase 1 of the first `/learn` (only if missing) |
| `study-progress.md` | Inside each study folder | Subject-matter knowledge for **this study only** — what the learner has demonstrated, where they are growing, what they still need | Phase 1 of every `/learn` |

---

## Boundary Rule

**Subject-matter knowledge → `study-progress.md`** (in the active study folder).
**Learner-as-a-person information → `learner-profile.md`** (at the root).

Concretely:
- "Understands backpropagation" → study progress (subject matter).
- "Strong at debugging by reading logs" → study progress if it surfaced while learning a specific topic; if you observe it as a *general* trait across multiple studies, also note it in the root profile under Observations.
- "Prefers concrete examples before abstract explanations" → root profile (learning style).
- "Has 10 years of Python experience" → root profile (general background).
- "Misconception that gradients accumulate by default in NumPy" → study progress (subject-specific).

When in doubt: ask whether the observation will still be relevant in a future study on a *different* topic. If yes → root profile. If no → study progress.

---

## A. Global `learner-profile.md` (root)

### When to Create
At the start of Phase 1 of the **first** `/learn` run, if the file does not already exist. Subsequent `/learn` runs read it and append a new entry to the Studies section.

### When to Update
- **First creation**: populate Identity, Background, and Learning Style from the motivation discovery and initial assessment.
- **End of Phase 1 of any `/learn`**: append a new entry to the Studies section with the new study's slug, objective one-liner, and status.
- **Anytime during a study**: if you observe a *cross-cutting* trait about the learner as a person (learning style, general programming maturity, what scaffolding works best), update the relevant section. Do **not** copy subject-matter findings here.
- **End of Phase 3**: update the corresponding study's status in the Studies section. If the study revealed something about the learner-as-a-person, update Observations.

### Structure

```markdown
# Learner Profile

## Identity
<!-- Name (if known), how they want to be addressed, anything else they have shared about themselves. -->

## Background
<!-- General programming maturity, prior experience, languages and tools they know well. -->
<!-- Format: - [YYYY-MM-DD] Description -->

## Learning Style
<!-- Preferred ways of learning: examples-first vs abstract-first, depth-first vs breadth-first, etc. -->
<!-- Format: - [YYYY-MM-DD] Description -->

## Observations
<!-- Cross-cutting observations: what kinds of hints work, pacing, attention patterns, motivation drivers. -->
<!-- Format: - [YYYY-MM-DD] Description -->

## Studies
<!-- Index of every study the learner has started. One line each. -->
<!-- Format: - [`<slug>`](./<slug>/learning-plan.md) — <objective one-liner> — Status: in-progress / completed / abandoned -->
```

---

## B. Study-level `study-progress.md`

### When to Create
At the end of Phase 1 of every `/learn`, **inside the new study folder**, populated with the results of the initial knowledge assessment scoped to this study's topic.

### When to Update
- **After the initial assessment**: populate Strengths, Emerging Skills, and Gaps from the assessment. Partial understanding goes to Emerging Skills, not Strengths.
- **During project work**: when reviewing in-progress code or answering questions. If the student applies a concept correctly without help, that's a demonstrated strength. If they can do it with guidance but not alone, it's an emerging skill. If it's beyond their reach even with help, it's a gap. Update in the moment — do not wait until the project ends.
- **After each post-project assessment**: promote emerging skills that became independent to Strengths. Move gaps that show partial progress to Emerging Skills. Add newly discovered gaps.
- **When correcting misconceptions**: log them. Misconceptions tend to resurface; tracking them helps watch for recurrence.

### Structure

```markdown
# Study Progress

## Demonstrated Strengths
<!-- Skills and concepts the student can apply independently without guidance, within this study's topic. -->
<!-- Format: - [YYYY-MM-DD] Description -->

## Emerging Skills (Zone of Proximal Development)
<!-- Skills the student has shown partial understanding of or can perform with guidance, but not yet independently. -->
<!-- These are the primary targets for project design — they represent the student's growth edge. -->
<!-- Format: - [YYYY-MM-DD] Description -->
<!-- When an emerging skill becomes independent, move it to Strengths with the new date. -->

## Knowledge Gaps
<!-- Topics or concepts that are beyond the student's current reach, even with guidance. -->
<!-- Format: - [YYYY-MM-DD] Description -->
<!-- When a gap shows partial progress (student can do it with help), move it to Emerging Skills. -->

## Misconceptions
<!-- Wrong mental models or recurring mistakes within this study's topic. -->
<!-- Format: - [YYYY-MM-DD] Description — Status: active / resolved -->
<!-- Keep resolved ones visible so the teacher can watch for recurrence. -->

## Observations
<!-- Study-specific observations: how the student is engaging with this topic, where they get stuck, etc. -->
<!-- Cross-cutting observations about the learner as a person belong in the root learner-profile.md instead. -->
```

Keep entries concise — one line per item. Always include dates so progress is visible over time.

---

## How to Use Both Documents

| Context | What to read | What to update |
|---|---|---|
| **Starting a new `/learn`** | Root `learner-profile.md` (full) — to know the learner as a person and what they have studied before | Root profile: append new study link. Study folder: create `study-progress.md`. |
| **Designing a project (Phase 2)** | Active study's `study-progress.md` — target emerging skills, reinforce recent strengths, introduce a controlled number of gaps. Also read root profile for learning style. | — |
| **Calibrating scaffolding (during project)** | Active study's `study-progress.md` — more support deep in the ZPD, less for skills approaching independence. | Update `study-progress.md` in the moment as new evidence appears. |
| **Answering a question (during project)** | Active study's `study-progress.md` — if it touches an emerging skill or misconception, invest more time. | Update `study-progress.md` if the answer reveals a new strength/gap/misconception. |
| **Writing evaluation questions (Phase 3)** | Active study's `study-progress.md` — probe emerging skills and misconceptions the project was supposed to address. | — |
| **Deciding if the study's objective is met (Phase 4)** | Active study's `study-progress.md` — all critical topics should be in Strengths with no blocking gaps remaining. | Mark study as `completed` in the root profile's Studies section. |
