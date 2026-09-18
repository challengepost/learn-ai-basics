# Spec Patterns — Agent Reference

For the agent only. This is your architecture knowledge base for `4-spec`: how to support informed learner choices, how to size a project against the learner and the POC boundary, how to simplify without losing the product, and how to explain any of it to someone who doesn't have the vocabulary yet.

## Help the Learner Choose, Without Choosing for Them

No prescribed stack catalog. Start from their PRD, coding experience, interests, and constraints. Ask for their technical direction before introducing options.

When they need help—even if they ask for a recommendation—give a manageable spread of genuinely viable alternatives. Explain each at comparable depth: purpose, capabilities, limitations, setup, learning demands, cost, and sharing implications. No preferred choice, ranking, or default. Ask which fits their priorities and why; let them decide.

Teach the vocabulary needed for a choice rather than demanding an uninformed guess. Keep every alternative proportional to a proof of concept. A new tool can be the learner's legitimate learning goal; accommodate it by reducing other complexity rather than expanding the product.

## The Complexity Budget

An informal read on whether this architecture is a coherent way for this learner to prove the idea — stretched but reachable, without avoidable cost or risk. **Not a rubric and not a score.** Weigh:

- **Demonstrated experience** — what they've actually built, and how much of it they did versus the AI.
- **Unfamiliar frameworks** — each one adds setup and debugging in a system whose error messages may mean nothing to them yet.
- **Number of separate services** — every additional service adds an account, a key, and a failure mode.
- **Authentication or payments** — both add substantial complexity and rarely prove the product idea.
- **Real-time or background behavior** — sync, websockets, cron, queues. Hard to build, harder to debug.
- **Deployment difficulty** — free and instant, or a multi-step configuration?
- **Paid, unreliable, or restricted dependencies** — cost, rate limits, waitlists, approval flows.

**Over budget looks like:** three or more services to wire up; a login screen before any feature exists; a framework nobody in the conversation has used; a data model with six tables; a dependency needing a paid plan or manual approval; a demo that only works after a deploy; or "and then it syncs live between users."

When the architecture overwhelms the POC, simplify its expression rather than hand-waving the complexity.

## The Simplification Playbook

Preserve the central idea. Use these substitutions to explain possible simplifications, not to decide for the learner. Agree on consequential changes, then record each in the spec with its reason. Label simulations and sample data clearly; never fake the kernel.

| Over budget | Simpler substitution that keeps the idea |
|---|---|
| Real accounts, passwords, sessions | A display name typed on first use, kept in local storage. Multi-person feel, no auth. |
| Multi-user real-time sync | One shared data file plus a refresh button, or a single-user version with sample data from "other people." |
| Hosted database with configured access rules | A local SQLite or JSON file. Same shape of data, same queries, no infrastructure. |
| Paid or rate-limited API on the critical path | A smaller free model, a cheaper endpoint, or seeded realistic sample data with the live call behind a flag. |
| Background jobs, cron, scheduled work | Do the work when the user opens the app or presses the button. Same output, visible timing. |
| File or image upload with cloud storage | Paste text, provide a URL, or read from a local folder. |
| Payments | A fake checkout screen that records the intent. The product idea is almost never the payment. |
| Deployment to a live URL | Run locally and record it — unless the learner said sharing a link matters, in which case pick the stack with the one-click deploy. |
| Email, SMS, or push notifications | Show it on screen, or write it to a file the learner can open. |
| Search over a large corpus | Search over a small curated set. Relevance is demonstrable at any scale. |

If a swap would kill `scope.md > The Unique Kernel`, it's the wrong swap. Find a different one, or cut a different feature.

## Explaining Architecture Without the Vocabulary

- **Walk one concrete journey through the system.** Describing components abstractly ("the frontend calls the API which queries the database") teaches nothing. Walking their actual behavior through it does: "You type the entry and hit save. That text goes into a file on your laptop called `entries.json`. When you open the app tomorrow, it reads that file back and shows you the list." Same architecture, and now they can repeat it.
- **Analogies that hold up:** a database is a spreadsheet the program reads and writes; an API is a form you submit to someone else's building and get a reply from; a server is a computer that's always on, waiting to be asked; `localStorage` is a sticky note the browser keeps for one site; a framework is a pile of decisions already made for you.
- **Name a thing, then use the name.** Introduce the term once with its plain meaning, then use it. Withholding vocabulary entirely leaves them unable to talk about their own app.
- **The failure mode is pseudo-explaining** — a fluent paragraph of jargon that sounds like an explanation and transfers nothing. Worse than silence, because it looks complete. If they couldn't say it back, you haven't explained it.
- **Teach during the decisions, not with an ending quiz.** Ask what they want to happen, explain unfamiliar mechanisms and alternatives, and invite questions. Use review to explore concerns and alignment, not to test recall.

## Diagramming

Use diagrams during the conversation and in visual planning companions. Tie every diagram to this project's actual behavior. **ASCII** works everywhere:

```
┌──────────┐     ┌──────────┐     ┌──────────┐
│ Frontend │────→│   API    │────→│ Database │
└──────────┘     └──────────┘     └──────────┘
```

**Mermaid** renders more richly in many tools:

```mermaid
graph LR
  Frontend --> API --> Database
```

Pick whichever is clearest for the specific diagram. Don't make the learner choose a format.

## File Structure Conventions

Always include a full annotated tree in the spec. `5-build` leans on it. Derive the tree from the learner's chosen architecture; the example below is illustrative, not a prescribed stack.

```
project/
├── src/
│   ├── components/    # UI components
│   ├── pages/         # Route-level pages
│   ├── lib/           # Shared utilities
│   └── api/           # API routes or client
├── devpost/           # Devpost learning workspace
├── package.json
└── README.md
```

The learner should be able to read the tree and know where everything lives.

## Data Flow Documentation

For any app that holds data, document how it moves:
1. Where does it originate? (User input, external API, file.)
2. Where is it stored?
3. How does it get from A to B?
4. What transforms along the way?

Keep it pragmatic — a short narrative or one diagram. No formal DFDs.

### State: where data lives

The single biggest source of confusion during a build. For every piece of data the app touches, the answer must exist in the spec: *where is this stored, how does it get updated, and what happens when the user navigates away and comes back?* **Do not use the phrase "state management"** with a learner who wouldn't recognize it — just ask the three questions in plain language.

## API and Service Contracts

For every external service, spell out the exact calls: endpoint, payload, response shape, auth method. Include doc links. This is the difference between a build that flows and a build that stalls while the agent reverse-engineers an API.

Where research is available, verify current versions, pricing, rate limits, and whether the library is still maintained, and share the links with the learner — modeling that habit is part of the lesson. Where it isn't, reason from what you know, **state your uncertainty explicitly**, and list the specific things to verify early in the build. Never imply a lookup happened when it didn't. A useful spec must be reachable with no network access.

## Error Boundaries and Fallbacks

Not exhaustive error handling. The two or three places this will actually break in front of someone: the API is slow, the data is empty, the input is strange. Pick a simple response for each — a loading state, a plain message, seeded sample data — and write it down.

## How Another Person Tries It

This is the durable version of "demo readiness," and it drives real architecture decisions.
Submission requires a short demo video and a public GitHub repository. Reviewers should not need to clone the repo to see the proof.
- **Local app + recording:** sufficient; document startup and what to show, then upload the recording and check access.
- **Optional deployed URL:** lets others try it directly in addition to the required video and repository; record any chosen hosting target, setup, costs, and deploy steps.

Explain hosting tradeoffs only if relevant and record the learner's choice. They can change optional deployment plans in `6-ship`; keep the architecture proportional to the proof.

## Section Depth and Traceability

`5-build` must be able to point at a specific part of the spec, which means anything it will reference needs its own heading. That is the whole requirement — **depth follows the product's actual complexity, not a ceremony quota.** A single-file CLI tool may need two levels; a full-stack app with several surfaces may need four. A wall of empty headings is worse than a flat document.

Reference PRD headings by name to keep traceability, using whatever headings that PRD actually has: "Implements `prd.md > Finding recipes`" or "See `prd.md > States and Boundaries` for the empty-state behavior." During the build, the agent can then look up both what to build and what it should do.

## Spec Self-Review

After drafting, review your own work for:
- Ambiguities that would confuse the build ("what exactly does 'handle auth' mean here?").
- PRD requirements with no home in the architecture.
- Complexity that does not help prove the POC ("six tables for a simple single-user tool").
- Internal inconsistency between the data model, the file tree, and the components.
- Failure points with no fallback.

If the harness supports an independent review pass, use one; otherwise do it directly. Fix internal inconsistencies yourself. Ask the learner only about consequential decisions that remain unresolved, with no quota of findings or questions. The learner review is one "does this look good, or would you change anything?" exchange, not another interview or second sign-off.
