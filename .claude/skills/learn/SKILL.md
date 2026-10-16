---
name: learn
description: Start a new study in this learning home. Run from the learning home root with the topic as the argument.
argument-hint: <topic>
disable-model-invocation: true
---

The student wants to start a new study. Their learning topic is:

> $ARGUMENTS

Read the following files to understand your role and methodology:
- `CLAUDE.md` — Your role, core rules, and how to determine where you are in the learning home.
- `learning-method.md` — Full teaching methodology (Phase 1 details below).
- `evaluation-method.md` — How to conduct evaluations.
- `learner-profile-spec.md` — How to create and maintain `learner-profile.md` (root) and `study-progress.md` (per study).

**Precondition:** verify that the current directory is the root of a learning home by checking that `learning-method.md` exists in the cwd. If it does not exist, refuse and tell the student that `/learn` must be invoked from the root of a learning home.

Now begin **Phase 1: Discovery & Planning** for a new study. The student has already told you the topic. Do NOT ask them what they want to learn — they just told you. Follow the steps in `learning-method.md` Phase 1, summarized here:

1. **Create the study folder.** Derive a descriptive slug from the topic above (e.g., "train neural networks in PyTorch" → `train-neural-networks-pytorch/`) and create it at the root of the learning home. All study-specific files for the rest of this phase live inside it.
2. **Discover the student's motivation** — *why* they want to learn this. The motivation is the most important input and will shape everything else (objectives, topics, projects). Do not move on until you understand it clearly.
3. **Read `learner-profile.md` if it exists at the root.** Use the learner's general background, learning style, and prior studies to calibrate the next step — skip baseline questions about things already established.
4. **Conduct the initial knowledge assessment** following `evaluation-method.md` to gauge their current level on this study's topic.
5. **Update or create the global learner profile** at the root following Section A of `learner-profile-spec.md`. Create it if missing; otherwise update Background / Learning Style / Observations with anything new and cross-cutting you learned.
6. **Create `study-progress.md` inside the new study folder** following Section B of `learner-profile-spec.md`, populated with the assessment results scoped to this study's topic.
7. **Draft the learning plan and write `learning-plan.md` inside the study folder.**
8. **Append a new line to the Studies section of the root `learner-profile.md`** linking to this new study (slug, objective one-liner, status: in-progress).
9. **Iterate with the student** until they approve the plan.
