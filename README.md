# Learn AI Basics — skills

Devpost Learn hackathon curriculum, packaged as agent skills. Works in any harness that reads `SKILL.md` (Claude Code, Codex, Cursor, …).

## Install

```
npx skills add challengepost/learn-ai-basics --all -y
```

Prerequisites: **node** and **git** installed, and an empty folder set aside for your project.

## The sequence

| Skill | What happens | Output |
|---|---|---|
| `1-start` | Understand the six steps, check your workspace, and introduce your idea and experience | `devpost/learner-profile.md` |
| `2-scope` | Find or sharpen your idea, identify its kernel, define "done," and keep it proof-of-concept sized | `devpost/scope.md` |
| `3-prd` | Learner-led product interview grounded in scope: screens, layout, visual style, behavior, edge cases, and a firm now/later boundary. No code talk | `devpost/prd.md` |
| `4-spec` | How it's built—you lead; the agent explains neutral options and records your technical choices | `devpost/spec.md` |
| `5-build` | Verified, committed build steps, hands-on review and revisions, then a five-minute code tour | `devpost/checklist.md`, your app, `devpost/app-map.html` |
| `6-ship` | Prepare the required demo video and public GitHub repository, then write your own submission and exit-survey answers | video, public repository, learner-written submission |

**What to expect:** about 2–4 hours of active work, ending in a small working proof of concept — not a product. You learn one process: plan before you build through flipped interaction. The agent interviews, probes, and organizes; you supply the ideas and decisions. Scope, PRD, and spec each aim for roughly six meaningful exchanges, counting existing answers, then offer more exploration or draft review. A clear "looks good" approves a displayed plan—no second sign-off. PRD includes 1–2 relevant design questions so visual choices don't default to generic AI styling. Optional HTML companions for scope, PRD, and spec use diagrams and interactive reveals—not just rendered Markdown. The build checklist stays Markdown-only. Speech-to-text helps a lot.

**Build modes:** learn mode includes a hands-on check and code orientation after every slice. Fast mode reduces explanation but still pauses three times for you to run the app, explore, and give feedback. Both end with a kick-the-tires review and agreed revisions, then a five-minute code tour: follow one action through 2–3 real code locations in your editor, try one optional tiny edit, and receive a standalone app map. This helps close the gap between having AI-written code and understanding what you own; it is not a quiz.

**Shipping:** a short demo video **and** a public GitHub repository are required; deployment and peer feedback are optional. Write your own project name, short description, other submission fields, and exit-survey answers. The agent can interview you and identify gaps, but only correct spelling and grammar in your copy—never draft or rewrite it. Any optional Discord post or peer feedback must also be human-written. Before publishing, check files and history for secrets and private context, especially `devpost/learner-profile.md`. Finish by submitting on Devpost.

Invoke each skill by name in your agent. Starting a fresh conversation between skills is fine — the `devpost/` files carry the context forward.

## Layout

```
skills/<name>/SKILL.md          the skill
skills/<name>/templates/        document templates the skill fills in
skills/<name>/references/       deeper material the skill reads on demand
```

## How progress is tracked

There is no separate progress file. The `devpost/` folder is the state:

- Each planning document (`scope.md`, `prd.md`, `spec.md`, `checklist.md`) carries `status: draft | approved` in its frontmatter. Skills save a draft as soon as one exists and flip it to `approved` when the learner clearly approves the displayed plan. "Looks good" counts; silence does not, and no second sign-off is needed.
- `learner-profile.md` is about the learner, never about progress. It exists or it doesn't.
- `checklist.md` tracks slices, three hands-on checkpoints, the final review, and the code tour/app map through its `- [ ]` / `- [x]` boxes, plus the git log. Checked slices alone do not mean the build is complete.

Every skill opens by listing `devpost/`, reading those status lines, saying back where the learner is, and routing — forward to the right skill if they're behind, or to the first unfinished thing if they're mid-way. So a fresh conversation at any point costs nothing.
