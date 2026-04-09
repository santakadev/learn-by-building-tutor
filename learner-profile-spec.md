# Learner Profile Specification

`learner-profile.md` is a **living document** at the root of the learning workspace. It tracks the student's demonstrated knowledge, skills, and gaps as they progress. It is the teacher's primary reference for deciding what to teach next, how to guide, and what projects to design.

---

## When to Create

Create `learner-profile.md` at the end of the **initial knowledge assessment** (Phase 1, step 2). Populate it with the assessment results.

## When to Update

Update the profile whenever you observe new evidence about the student's abilities:

- **After the initial assessment** — populate strengths, emerging skills, and gaps from evaluation results. Partial understanding goes to Emerging Skills, not Strengths.
- **During project work** — when reviewing in-progress code or answering questions. If the student applies a concept correctly without help, that's a demonstrated strength. If they can do it with guidance but not alone, that's an emerging skill. If it's beyond their reach even with help, that's a gap. Update the profile in the moment — do not wait until the project ends.
- **After each post-project assessment** — update based on evaluation results. Move emerging skills that became independent to Strengths. Move gaps that show partial progress to Emerging Skills. Add newly discovered gaps.
- **When correcting misconceptions** — log them. Misconceptions tend to resurface; tracking them helps watch for recurrence.

## Structure of `learner-profile.md`

```markdown
# Learner Profile

## Demonstrated Strengths
<!-- Skills and concepts the student can apply independently without guidance. -->
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
<!-- Wrong mental models or recurring mistakes. -->
<!-- Format: - [YYYY-MM-DD] Description — Status: active / resolved -->
<!-- Keep resolved ones visible so the teacher can watch for recurrence. -->

## Observations
<!-- Learning pace, preferred learning style, what types of hints work best, etc. -->
```

Keep entries concise — one line per item. Always include dates so progress is visible over time.

## How to Use

| Context | How the profile informs your decision |
|---|---|
| **Designing a project (Phase 2)** | Target emerging skills as the primary focus. Reinforce recent strengths. Introduce a controlled number of new concepts from gaps into the ZPD. Avoid projects that only exercise what the student already knows. |
| **Calibrating scaffolding (during project)** | More support for skills deep in the ZPD (recently moved from gaps). Lighter nudges for emerging skills approaching independence. Minimal intervention for strengths. |
| **Answering a question (during project)** | If it touches an emerging skill or misconception, invest more time. If it touches a strength, give a lighter nudge. |
| **Writing evaluation questions (Phase 3)** | Probe emerging skills and misconceptions the project was supposed to address. Check whether emerging skills have become independent. |
| **Deciding if the objective is met (Phase 4)** | All critical topics should be in Strengths with no blocking gaps or emerging skills remaining for the core objective. |
