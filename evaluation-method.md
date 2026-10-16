# Evaluation Method

This document describes how to conduct evaluations using Claude Code's interactive tools.

---

## When to Evaluate

There are two evaluation moments in the learning process:

1. **Initial Knowledge Assessment** (during Phase 1) — after discovering the student's goals but **before** writing the learning plan. Purpose: gauge the student's current level so the plan is properly calibrated.
2. **Post-Project Assessment** (during Phase 3) — after the student says they finished a project. Purpose: verify that the project's learning goals were understood, not just implemented.

---

## Evaluation Procedure

### Step 1 — Enter Plan Mode

Call `EnterPlanMode` to begin the evaluation session. This gives you an interactive loop to ask questions and process answers without writing code.

### Step 2 — Ask Questions

Use `AskUserQuestion` to present questions. Ask them **one at a time** (or in small batches of up to 4) so you can adapt subsequent questions based on previous answers.

There are two question formats:

#### Multiple Choice

Use when there is a set of predefined answers to choose from.

- Each option: `label` = the choice text, `description` = `"-"` (always).
- Use 2 to 4 options.
- Set `multiSelect: false`.

Example:

```json
{
  "question": "What does the borrow checker enforce in Rust?",
  "header": "Q1",
  "options": [
    { "label": "Memory safety at compile time", "description": "-" },
    { "label": "Garbage collection at runtime", "description": "-" },
    { "label": "Type inference", "description": "-" }
  ],
  "multiSelect": false
}
```

#### Free Form

Use for open-ended questions where the student should write their own answer.

- Present exactly **2 options**:
  1. `label`: `"Type your answer (select Other)"`, `description`: `"-"` — instructs the student to select the **Other** option (automatically added as the 3rd choice by Claude Code) to type their response.
  2. `label`: `"I don't know"`, `description`: `"-"`
- Set `multiSelect: false`.

Example:

```json
{
  "question": "Explain in your own words what ownership means in Rust.",
  "header": "Q2",
  "options": [
    { "label": "Type your answer (select Other)", "description": "-" },
    { "label": "I don't know", "description": "-" }
  ],
  "multiSelect": false
}
```

The student will see three choices: "Type your answer (select Other)", "I don't know", and "Other". They select **Other** to type their free-form answer.

### Step 3 — Evaluate and Adapt

- After each answer (or batch), decide if you need follow-up questions to probe deeper.
- If the student answers "I don't know", note the gap but do not penalize — use it to calibrate the plan or identify what needs reinforcement.
- For wrong multiple-choice answers, consider asking a follow-up to understand their reasoning before marking it as a gap.
- Adapt difficulty: if the student is getting everything right, ask harder questions. If they are struggling, simplify.

### Step 4 — Write Results and Exit Plan Mode

After all questions are done:

1. Write the evaluation summary to the plan file. Include:
   - Demonstrated strengths.
   - Identified gaps or misconceptions.
   - **For initial assessment:** how the results should shape the learning plan (difficulty level, topics to emphasize or skip). The findings will be written into the new study's `study-progress.md` (and any cross-cutting traits into the root `learner-profile.md`) once Phase 1 continues.
   - **For post-project assessment:** whether each of the project's learning goals (from `PROJECT.md`) was met, and any topics that need reinforcement in the next project. The findings will update the active study's `study-progress.md`.
2. Call `ExitPlanMode` to present the evaluation results to the student.

---

## Question Design Guidelines

- Ask about **concepts and reasoning**, not trivia or syntax memorization.
- **Initial assessment:** cover breadth to map the student's knowledge landscape. Aim for **5–10 questions**.
- **Post-project assessment:** focus on the specific learning goals defined in `PROJECT.md`. Aim for **3–7 questions**.
- Mix multiple choice and free form. Use free form for questions that require deeper conceptual understanding.
- Do not ask trick questions. The goal is to understand what the student knows, not to trip them up.
- Order questions from easier to harder within an evaluation.
