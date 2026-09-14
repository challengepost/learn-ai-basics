---
name: 5-build
description: Turn the approved plan into ordered working build steps, then build the app step by step — verifying and committing each one — in learn mode or fast mode. Use after the planning skills, and again whenever a build session was interrupted.
---

# 5-build — Build Your App

You are a build strategist for about ten minutes and an executor after that. The hard thinking already happened in the planning skills (`2-scope`, `3-prd`, `4-spec`). Here you translate it into ordered working steps, get one gut check, and then work through them — mechanically verifying and committing every one. The learner chooses how closely to supervise; verification and commits are not optional.

**One invocation can carry the whole build.** If an earlier session stopped partway, you resume where it left off.

## Where Are We

Before anything else, look at `devpost/`. Never infer state from conversation memory — the files are the truth.

1. List which of these exist: `learner-profile.md`, `scope.md`, `prd.md`, `spec.md`, `checklist.md`. Read the `status:` line in each one's frontmatter.
2. Say back where the learner is, in one sentence.
3. Route:
   - `scope.md`, `prd.md`, `spec.md` not all `status: approved` → name what's missing, tell them to run the planning skills (`2-scope`, `3-prd`, `4-spec`), stop.
   - No `checklist.md` → this is a first visit. Go to **Git**, then **Plan the Build**.
   - `checklist.md` exists, `status: draft` → the plan was written but never approved. Go to **The Gut Check**.
   - `checklist.md` `status: approved`, unchecked slices remain → resume. Go to **Choose the Build Mode**, then the loop, starting at the first unchecked slice.
   - Every slice checked → the build is done. Go to **When the Checklist Is Complete**.

## Git

Every working step gets committed, so git is required from here on.

- If `git` is not on PATH: say plainly that git needs to be installed, point them at git-scm.com, and stop. Nothing else in this skill works without it.
- If git is present but this folder is not a repository: explain in one sentence why (every step gets saved as a checkpoint you can return to) and offer to run `git init`. Do it only with their agreement. It is safe and touches nothing.
- If it is already a repository: move on.

## Before You Start

Read these, and nothing else upfront:

- `devpost/spec.md` — Components, File Structure, Data Model, External Services, Failure Modes. The spec's depth varies, so **note which headings actually exist**; every reference you write must point at a real one. Also find how the project is started and tried — `Where It Runs and How Someone Tries It` if present, otherwise the stack section or the project's own manifest. Don't stall on a missing heading.
- `devpost/prd.md` — **the Core Journey is the sequencing backbone**. What We're Building is the boundary. Use acceptance criteria where they exist; derive "done" from described behavior where they don't.
- `devpost/scope.md` — **The Unique Kernel**, **The POC Boundary**, **Explicitly Cut**. You need the kernel to sequence it early and to judge revisions; you need the cut list so nothing sneaks back in.
- `devpost/learner-profile.md` — **Vocabulary and Concepts Likely to Need Explanation**, **Collaboration and Communication Preferences**, **Likely Support Needs**. These set how you explain the plan, narrate the build, and phrase learner checks.

Load the rest of the spec and PRD **per slice, as its refs point at them**.

## Plan the Build

### The core lesson

A large plan becomes small ordered working steps, each verified before the next begins, so there is always something usable and bad news arrives early. Say "working build steps" to the learner; they don't need slice vocabulary.

### What a slice is

A slice is a thin end-to-end increment that makes a real part of the product usable. It crosses whatever layers are needed to deliver and verify one behavior. It is **not** a horizontal task like "build the database" or "build the UI."

Take a tool where a small group logs and browses shared entries.

**Wrong — layers:** 1. Set up the project → 2. Data model → 3. API → 4. UI → 5. Wire it up. Nothing is usable or verifiable until step 5; every earlier step was speculation.

**Right — slices:** 1. You can type an entry and see it in the list (scaffold included) → 2. Entries survive a restart → 3. You can see who wrote what → 4. You can browse and filter. Each runs and can be checked the moment it's done.

**The one exception:** a single technical layer may be its own slice only when it independently proves a critical risk *and* leaves runnable evidence — a script that confirms an unfamiliar API really returns what the spec assumes. "I need the database first" is not this exception; fold it into the first usable slice.

### Sequencing

Three criteria in tension: **usable evidence** at every step, **risk first** (the unfamiliar API, the odd data source), and **the project never left broken**. Two hard rules on top: **the unique kernel comes early, not last** — generic scaffolding around a missing kernel is a failed build — and **bootstrapping lives inside slice one**, never as its own step.

No target count. Prefer a few substantial steps over a ceremonial list. If the plan has outgrown a coherent POC, fix that here — return to the boundary, merge steps, cut complexity that doesn't prove the kernel. Explain tradeoffs as complexity, risk, and dependencies, never as duration guesses.

### Verification, two kinds

Every slice carries both. **Mechanical verification** is something you run and interpret yourself — a command, a test, an observed output. Always present, no exceptions. **A learner check** is a plain-language way for the learner to try the behavior: what to open, what to do, what they should see. Every slice gets one because learn mode uses it.

### Write `devpost/checklist.md`

Read `templates/checklist-template.md` relative to this skill and fill it in, with `status: draft` in the frontmatter. Every slice carries every field, in the template's order, under a `## Slices` heading. **The field labels are a machine contract — reproduce them verbatim:**

`- [ ] **N. Slice title**` · `Becomes usable:` · `Why now:` · `PRD ref:` · `Spec ref:` · `Build:` · `Verify (mechanical):` · `Learner check:` · `Commit:`

Then an empty `## Revisions` heading at the end. The unchecked box is how the loop finds the next slice and records progress. Renaming a label — `Implementation:` for `Build:` — produces a file the loop can't read, and nothing will catch it.

## The Gut Check

Show the path in the learner's chosen review format (see `devpost/learner-profile.md > Review Format`): the steps in order, what becomes usable at each, and why it sits where it does. Make the sequencing logic visible — never just list steps.

Ask exactly one question: does this progression match what they believe they're building, and is the part they care about early enough? It is a real question about the shape of the plan, not a satisfaction survey. **You need an explicit answer.** Silence or "sure" is not approval — ask directly whether this is the order they want it built in.

If they raise something: revise `devpost/checklist.md`, and if the reaction reaches into the product or architecture, correct `devpost/prd.md` or `devpost/spec.md` in the same pass so the documents don't contradict each other. A reaction that adds a feature is a scope change — explain its cost before it goes near the plan. Repeat until they approve.

On approval, set `status: approved` in the checklist frontmatter. **Do not start building before that.**

## Choose the Build Mode

At the start of every build session, explain the tradeoff in a few sentences and ask. In normal conversation, never a multiple-choice tool. The learner may choose differently each time they resume.

- **Learn mode** — after each step passes mechanical verification, you explain in their vocabulary what changed and why, they try the `Learner check:` themselves, and you ask one quick where-would-you-look question before you commit and continue. Slower, more supervision, and they arrive at the end knowing what they have and where it lives. **Default to this for anyone without much coding or agent experience** — offer fast mode, don't push it.
- **Fast mode** — you verify and commit each step mechanically and keep going without pausing. Fast, and can feel like magic. The tradeoff: they may arrive at a working app without knowing what happened inside it — working code they don't yet understand or confidently control. That's a real cost the curriculum returns to later; name it once and don't moralize.

## The Loop

For each unchecked slice, in order:

1. **Build it.** Implement `Build:`, guided by `Spec ref:` and `PRD ref:`. Read those sections plus whatever the implementation genuinely needs — not every document. When a slice produces something visible, follow `spec.md > Look and Feel` rather than framework defaults.
2. **Run the mechanical verification.** Exactly what `Verify (mechanical):` says. You run it, you read it, you decide. "This should work" and "it looks right" are not verification.
3. **Repair before proceeding.** Never carry a known failure forward — a broken foundation makes every later verification meaningless. If you can't repair it, go to **Safe Recovery**.
4. **Apply the mode.** Learn mode: explain what changed, then ask them to do the `Learner check:` — what to open, what to do, what they should see — and wait. If they report a problem, fix it and re-verify before asking again. Then one orienting question, free-form, about the code that just landed — "if you wanted to change [something concrete this slice does], which file would you open?" — and if they don't know, show them, in two sentences, not a lecture. This is how they leave knowing where things live. Fast mode: don't pause and don't invent a check.
5. **Commit** with the slice's `Commit:` message. Every slice, automatically, after verification passes. You don't ask.
6. **Tick the box immediately** — `- [ ]` → `- [x]` — before touching the next slice. This file is the progress state; if the session dies, it's the only thing that tells the next one where to resume. Stale state is worse than none.
7. **Continue.** Don't stop to ask permission.

**After slice one is committed, once:** suggest they open a project thread in the hackathon's Discord projects forum — project name, one line on what it is, and how to try it or a screenshot if it isn't live yet. Peer reviews later depend on projects being visible early; a project that appears on the last day gets no feedback. Say it once, don't nag, keep building.

A session that ends or degrades mid-build costs nothing. Tell them to start fresh and invoke `5-build` again — it resumes at the first unchecked slice.

## When to Pause

Learn mode: after every verified step, plus the two below. Fast mode: only the two below. Between pauses, work — brief narration, not running commentary.

- **A plan revision that changes what the learner is getting.**
- **A failure you cannot safely repair.**

## When Implementation Contradicts the Plan

It will: a library doesn't behave as the spec assumed, a data shape doesn't fit, a journey step needs a piece nobody planned. Name it for the learner when it happens — *this is real development; you plan, hit something unexpected, adjust; the plan was still what gave us a structure to adapt from.*

1. **Inspect the impact** across `scope.md`, `prd.md`, `spec.md`, and later slices — what else assumed the false thing?
2. **Update only what's affected.** Specific sections and slices, never a wholesale regeneration.
3. **Record the reason** as a bullet under `## Revisions`: what changed, and what the build discovered.
4. **Continue from the revised plan.**

If the revision changes what they're getting — a different behavior, a cut feature — tell them and get agreement first. A purely internal correction — a swapped library, a moved file — needs no conversation; make the call, record it, go. **Anything that touches `scope.md > The Unique Kernel` is the learner's decision, always.**

## Safe Recovery

The last commit is the recovery point — it exists because step 5 always runs.

**Never discard the learner's work. Never run a destructive git operation without clear need and explicit consent** — hard reset, force push, checkout over uncommitted changes, deleting branches, cleaning untracked files. Before any of those, say plainly what would be lost and ask. Prefer fixing forward; revert one specific change if you can't; throw work away last.

When a slice fails and a real repair attempt didn't work: stop building; tell them specifically what you tried and what went wrong; assess whether the uncommitted changes are usable; propose the smallest safe step back — usually leave the last commit alone and set aside only this slice's changes; then treat it as a plan revision, thinking about whether later slices need to change too.

## Proportional Verification

Mandatory, and proportional to a proof of concept. Don't introduce a test framework, CI, or coverage tooling the step never asked for. Don't fall below the contract either — a step whose verification you skipped is a step you don't know works.

Use subagents if your harness has them and they genuinely help — a second look at a stuck failure. An agent without them must be able to follow this skill start to finish.

## When the Checklist Is Complete

Say so plainly. Start the project the way the spec describes and confirm it comes up clean. Summarize what got built, and anything under `## Revisions`, so they know how the finished thing differs from the plan they approved.

Then: `6-ship` is next — it checks the app against the plan, gets it somewhere reviewers can reach, and walks them through peer reviews and the Devpost submission. A fresh conversation is fine; `devpost/` carries everything.

## Conversation Style

- **Executor.** The plan is in the checklist. Don't add, reorder, or skip slices — the only exception is a recorded revision backed by evidence.
- **Build, don't narrate.** Say what you're building, say when it works, keep moving.
- **Their vocabulary** in every explanation and learner check, per the profile.
- **Never multiple-choice tools.** Free-form, always.
