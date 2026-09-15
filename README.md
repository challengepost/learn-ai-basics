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
| `1-start` | Short interview so the agent can pitch everything at your level | `devpost/learner-profile.md` |
| `2-scope` | The most important conversation: a long interview that pulls the idea out of your head, finds its kernel, defines "done," and cuts it to a proof of concept | `devpost/scope.md` |
| `3-prd` | Learner-led product interview grounded in scope: screens, layout, behavior, edge cases, and a firm now/later boundary. No code talk | `devpost/prd.md` |
| `4-spec` | How it's built—you lead; the agent explains neutral options and records your technical choices | `devpost/spec.md` |
| `5-build` | Verified, committed build steps with hands-on checkpoints in both modes, then a kick-the-tires revision round | `devpost/checklist.md`, your app |
| `6-ship` | Choose how to share (live URL or video), give two peer reviews, and write your own submission; the agent never drafts it | learner-written submission |

**What to expect:** about two hours, ending in a small working proof of concept — not a product. You learn one process: plan before you build through flipped interaction. The agent interviews, probes, and organizes; you supply the ideas and decisions. After thorough interviews, it writes the planning docs for your careful review. Optional HTML companions for scope, PRD, and spec use diagrams and interactive reveals—not just rendered Markdown. The build checklist stays Markdown-only. Speech-to-text helps a lot.

**Build modes:** learn mode includes a hands-on check and code orientation after every slice. Fast mode reduces explanation but still pauses three times for you to run the app, explore, and give feedback. Both end with a kick-the-tires review and agreed revisions.

**Shipping:** you can revisit video versus deployment after building. You must write your own submission fields, Discord post, and peer reviews. The agent can interview you and give feedback; for submission copy and your project post, it can correct spelling and grammar only—never draft or rewrite them. Completion requires two peer reviews, an accessible demo/video link, and your submission on Devpost.

Invoke each skill by name in your agent. Starting a fresh conversation between skills is fine — the `devpost/` files carry the context forward.

## Layout

```
skills/<name>/SKILL.md          the skill
skills/<name>/templates/        document templates the skill fills in
skills/<name>/references/       deeper material the skill reads on demand
```

## How progress is tracked

There is no separate progress file. The `devpost/` folder is the state:

- Each planning document (`scope.md`, `prd.md`, `spec.md`, `checklist.md`) carries `status: draft | approved` in its frontmatter. Skills save a draft as soon as one exists and flip it to `approved` only when the learner explicitly signs off.
- `learner-profile.md` is about the learner, never about progress. It exists or it doesn't.
- `checklist.md` tracks slices, three hands-on checkpoints, and the final review through its `- [ ]` / `- [x]` boxes, plus the git log. Checked slices alone do not mean the build is complete.

Every skill opens by listing `devpost/`, reading those status lines, saying back where the learner is, and routing — forward to the right skill if they're behind, or to the first unfinished thing if they're mid-way. So a fresh conversation at any point costs nothing.
