# Learn AI Basics — skills

Devpost Learning Hackathon curriculum, packaged as agent skills. Works in any harness that reads `SKILL.md` (Claude Code, Codex, Cursor, …).

## Install

```
npx skills add challengepost/learn-ai-basics --all -y
```

Prerequisites: **node** and **git** installed, and an empty folder set aside for your project.

## The sequence

| Skill | What happens | Writes |
|---|---|---|
| `1-start` | Short interview so the agent can pitch everything at your level | `devpost/learner-profile.md` |
| `2-scope` | The most important conversation: a long interview that pulls the idea out of your head, finds its kernel, defines "done," and cuts it to a proof of concept | `devpost/scope.md` |
| `3-prd` | Zoom in: the core journey, every behavior, edge cases, and a firm now/later boundary. No code talk | `devpost/prd.md` |
| `4-spec` | How it's built — one recommendation, calibrated to you; you leave able to explain your own app | `devpost/spec.md` |
| `5-build` | Plan becomes ordered build steps; the agent builds, verifies, and commits each one (learn or fast mode) | `devpost/checklist.md`, your app |
| `6-ship` | Give your two peer reviews, make the app reachable (live URL or video), draft your Devpost submission | submission text |

**What to expect:** about two hours, ending in a small working proof of concept — not a product. You learn one process: plan hard before you build, by letting the agent interview you (flipped interaction). Speech-to-text helps a lot.

Invoke each skill by name in your agent. Starting a fresh conversation between skills is fine — the `devpost/` files carry the context forward.

## Layout

```
skills/<name>/SKILL.md          the skill
skills/<name>/templates/        document templates the skill fills in
skills/<name>/references/       deeper material the skill reads on demand
```

## How progress is tracked

There is no progress file. The `devpost/` folder is the state:

- Each planning document (`scope.md`, `prd.md`, `spec.md`, `checklist.md`) carries `status: draft | approved` in its frontmatter. Skills save a draft as soon as one exists and flip it to `approved` only when the learner explicitly signs off.
- `learner-profile.md` is about the learner, never about progress. It exists or it doesn't.
- `checklist.md` tracks the build itself through its `- [ ]` / `- [x]` boxes, plus the git log.

Every skill opens by listing `devpost/`, reading those status lines, saying back where the learner is, and routing — forward to the right skill if they're behind, or to the first unfinished thing if they're mid-way. So a fresh conversation at any point costs nothing.
