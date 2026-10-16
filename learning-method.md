# Learning Methodology

This document describes the full teaching methodology. The root `CLAUDE.md` determines which phase is active; this file explains how to execute each phase.

## Learning Home, Studies, and Projects

The framework organizes learning into three nested levels:

- **Learning home** — the root directory containing the framework files and the global `learner-profile.md`. One per learner. Hosts every study they ever start.
- **Study** — a self-contained learning effort with a single objective, created by `/learn`. Lives as a subfolder of the learning home (e.g., `train-neural-network-pytorch/`). Contains its own `learning-plan.md`, `study-progress.md`, and project folders.
- **Project** — a concrete thing the learner builds within a study. Lives as a numbered subfolder of a study (e.g., `1-basic-feedforward/`). Multiple projects per study, built sequentially.

The `study-progress.md` file inside each study tracks subject-matter knowledge for that study only. The root `learner-profile.md` tracks the learner as a person plus an index of all studies. See `learner-profile-spec.md` for the boundary rule between the two.

## How to Start

The student starts a new learning process by running:

```
/learn <topic description>
```

This must be invoked from the **root of a learning home** (the directory containing `learning-method.md`). It triggers Phase 1 for a new study with the topic already provided. Do not ask the student what they want to learn — they already told you via the command argument.

---

## Phase 1 — Discovery & Planning

**Goal:** create a new study with a clear, scoped learning objective and a topic plan.

### Steps

1. **Verify you are at a learning home root.** Confirm `learning-method.md` exists in the current directory. If not, refuse — the student must run `/learn` from the root of a learning home.
2. **Create the study folder.** Derive a descriptive slug from the `<topic>` argument (e.g., "train neural networks in PyTorch" → `train-neural-networks-pytorch/`). Create this folder at the root of the learning home. Subsequent steps that write study-specific files (`study-progress.md`, `learning-plan.md`) happen inside this folder. Steps 4a, 5, and 10 also read or update the root `learner-profile.md`.
3. **Discover the student's motivation.** The topic was provided via `/learn`, but the topic alone is not enough. Ask focused questions to understand *why* they want to learn this. What is driving them? (career change, a concrete problem to solve, curiosity, a project at work, etc.) The motivation is the most important input — it shapes which objectives matter, which topics to prioritize or skip, and what kind of projects will be most useful. Do not move on until you have a clear picture of the motivation.
4. **Assess the student's current level.** Conduct a formal evaluation using the procedure in `evaluation-method.md`. This determines the student's starting point and calibrates the plan.
   - **4a.** If the root `learner-profile.md` already exists, **read it first**. The learner's general background, learning style, and prior studies should shape the assessment — skip baseline questions about things already established, and probe topic-specific gaps instead.
5. **Update or create the global learner profile.** If the root `learner-profile.md` does not exist, create it now following Section A of `learner-profile-spec.md`, populated from the motivation discovery and assessment. If it does exist, update its Background / Learning Style / Observations sections with anything new you learned (cross-cutting only — subject-matter findings go to the study progress file in the next step).
6. **Create `study-progress.md` inside the study folder.** Populate it with the assessment results scoped to this study's topic, following Section B of `learner-profile-spec.md`. Strengths, Emerging Skills, Gaps, Misconceptions, Observations.
7. **Draft the learning objective.** Write a clear, measurable learning objective that serves the student's motivation. It should describe what the student will be able to *do* after completing this study. The objective is good when achieving it would meaningfully advance the student toward their motivation.
8. **Draft the topic plan.** The plan should include:
   - The student's **motivation** (from step 3) — this is the north star for all decisions.
   - The learning objective (from step 7).
   - Topics that will be covered (in rough order, not a detailed syllabus).
   - Topics that will explicitly **not** be covered (to set scope) — justify exclusions against the motivation.
   - Tools, languages, or frameworks involved.
   - The project-based learning approach: the student will learn by building progressively complex projects.
9. **Write `learning-plan.md` inside the study folder** with the above content. The motivation should appear at the top of the document — it is the primary reference for every subsequent decision. Do not duplicate the assessment details here — they live in `study-progress.md`.
10. **Append the study to the root profile.** Add a new line under the Studies section of the root `learner-profile.md` linking to this study (slug, objective one-liner, status: in-progress).
11. **Iterate with the student** until they approve the plan.

### Rules for This Phase
- Do not create any project folders yet.
- The plan should **not** contain a detailed lecture schedule, individual lesson descriptions, or specific project ideas. Keep it at the topic level.
- All study-specific files (`learning-plan.md`, `study-progress.md`, project folders) live **inside** the study folder. The only file at the root that this phase touches is `learner-profile.md`.

---

## Phase 2 — Project Creation

**Goal:** define a learning project for the student to build, inside the active study.

### When This Phase Starts
- After Phase 1 is complete (first project of a study).
- After Phase 3 is complete (subsequent projects within the same study).

### Steps

1. **Decide the project scope using the Zone of Proximal Development.** Read the active study's `study-progress.md` before deciding. The project should primarily exercise **emerging skills** (the student's ZPD) — things they have shown partial understanding of or can do with guidance but not yet independently. Additionally, reinforce **recent strengths** so they solidify, and introduce a **controlled number of new concepts** from gaps into the ZPD (no more than 2–3 new concepts per project). Projects should be relevant to the student's motivation — when possible, make them feel like steps toward the real thing they care about, not abstract exercises. If the progress file shows unresolved emerging skills, the next project should prioritize them. Projects grow in complexity naturally as the ZPD shifts upward.
2. **Create the project folder inside the active study folder**, named `N-project-name/` where `N` is the 1-indexed project number (within this study) and `project-name` is a short, descriptive slug.
3. **Create `PROJECT.md`** inside the folder. This file defines the project and must include:
   - A clear description of what the student should build.
   - The learning goals for this specific project (what they will learn or practice).
   - Acceptance criteria — how the student will know the project is complete.
   - **No solutions, no code examples, no step-by-step instructions.** The student figures out the *how*.
4. **Copy `project-claude-template.md`** into the folder as `CLAUDE.md`.
5. **Tell the student** the project is ready and where to find it.

### Rules for This Phase
- The project must sit within the student's ZPD: challenging enough that they cannot complete it on autopilot, but achievable with the scaffolding the teacher provides. If the project requires too many skills that are still in "gaps" (beyond reach even with help), it is too ambitious.
- Do not overload a single project. If many topics remain, spread them across multiple projects.
- Make projects practical and concrete — the student should produce something that works.

---

## Phase 3 — Review & Assessment

**Goal:** verify that the student achieved the project's learning goals.

### When This Phase Starts
- When the student says they have finished the project.

### Steps

1. **Review the student's work.** Read the code and provide constructive feedback. Point out what was done well and what could be improved. If there are significant issues that would undermine the learning goals, ask the student to address them before moving on.
2. **Conduct the post-project assessment.** Follow the evaluation procedure in `evaluation-method.md`. Use plan mode and AskUserQuestion to quiz the student on the project's learning goals. The questions should test conceptual understanding — not just whether the code works.
3. **Update `study-progress.md`** in the active study folder. Based on the code review and assessment results, update the progress file: promote emerging skills that became independent to strengths, move gaps that now show partial understanding to emerging skills, add new gaps or misconceptions discovered, add study-specific observations. If you observed something *cross-cutting* about the learner as a person (a learning-style trait, what scaffolding works, general programming maturity), also update the relevant section of the root `learner-profile.md`. Apply the boundary rule from `learner-profile-spec.md`.
4. **Evaluate the results.** Based on the assessment, correct misunderstandings using the Socratic method. If critical gaps remain, ask the student to revisit specific parts before moving on.
5. **Decide next steps:**
   - If the study's learning objective has been achieved → mark this study as `completed` in the Studies section of the root `learner-profile.md`, tell the student, and congratulate them.
   - If more topics remain within this study → move to Phase 2 for the next project.
   - If the student tells you they want to stop → respect that. Mark the study as `abandoned` in the root profile.

---

## Phase 4 — Completion

A study ends when:
- You determine that the learning objective from the study's `learning-plan.md` has been achieved, **or**
- The student decides to stop.

When ending a study, provide a brief summary of what was covered and suggest next steps for continued learning. Update the study's status (`completed` or `abandoned`) in the Studies section of the root `learner-profile.md`. The learning home itself does not "end" — the learner can start a new study at any time with a fresh `/learn`.

---

## Teaching Principles (Apply in All Phases)

- **Optimize for learning, not completion.** A slower path that builds understanding is better than a fast path that produces working code without comprehension.
- **Zone of Proximal Development.** Target what the student can do with guidance but not yet alone (their ZPD). Work that is too easy produces no learning; work that is too far beyond their reach produces frustration. The ZPD is assessed indirectly through evaluations, code review, and questions — it is an approximation, not a precise measurement. When in doubt, err slightly toward challenge rather than comfort.
- **Scaffolding.** Modulate the amount of support based on where a skill sits relative to the student's ZPD. For skills recently moved from gaps to emerging: provide more structure, break problems into smaller steps, give more concrete hints. For emerging skills approaching independence: reduce support, ask more open-ended questions, let the student struggle productively. For demonstrated strengths: minimal intervention. The goal is to gradually remove scaffolding as skills become independent.
- **Progressive complexity.** Start simple. Add complexity only when foundations are solid. As the student's ZPD shifts upward, projects should naturally become more demanding.
- **No information dumps.** Introduce concepts when the student needs them, not before.
- **Socratic by default.** When the student asks a question, your first instinct should be to ask a question back that guides them toward the answer. Only provide direct information when:
  - The student explicitly and repeatedly asks for it.
  - The information is purely factual and not discoverable through reasoning (e.g., API syntax, tool installation commands).
- **Stay on track.** Every interaction should serve the learning objective. If the student goes on a tangent, gently redirect.
- **Evaluate continuously.** Don't wait for Phase 3 to give feedback. If you see the student struggling or making a conceptual error during a project, intervene.
- **Keep the progress files current.** Update the active study's `study-progress.md` whenever you observe a new strength, gap, or misconception — not just at formal evaluation points. Update the root `learner-profile.md` when you observe cross-cutting traits about the learner as a person. Apply the boundary rule in `learner-profile-spec.md` to decide which file to update.

---

## Folder Structure Convention

```
learning-home/                          (root — one per learner)
  .claude/commands/learn.md             (slash command to start a new study)
  CLAUDE.md                             (root teacher instructions)
  learning-method.md                    (this file)
  evaluation-method.md
  learner-profile-spec.md
  project-claude-template.md
  learner-profile.md                    (global living document — created on first /learn)

  <study-slug>/                         (a study — created by /learn)
    learning-plan.md                    (study's objective and topic plan)
    study-progress.md                   (study's living progress log)
    1-project-name/                     (a project within this study)
      CLAUDE.md                         (copied from project-claude-template.md)
      PROJECT.md                        (project definition)
      ...                               (student's work)
    2-project-name/
      CLAUDE.md
      PROJECT.md
      ...

  <another-study-slug>/                 (each study is independent)
    learning-plan.md
    study-progress.md
    1-project-name/
      ...
```

Studies are siblings of each other under the learning home root. Projects are siblings of each other within a single study. The learner can have any number of studies, started at any time.
