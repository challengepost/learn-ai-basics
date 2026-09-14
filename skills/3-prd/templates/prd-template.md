---
doc: prd
status: draft
---
<!-- `status` is the progress state every skill reads. Write `draft` when you first save this file,
     and change it to `approved` only when the learner explicitly signs off. Never skip the draft save —
     an unsaved draft dies with the conversation. -->

<!-- This is the complete product definition: the scope sketch, filled in. Adapt it
     to the product. Drop any section that doesn't apply, and add sections this product
     needs. Completeness is the standard, not length — a short PRD for a small product
     is correct. Keep it inside the approved POC boundary.

     Keep heading names stable and descriptive: `4-spec` and `5-build` reference
     them by name. -->

# [Project Name] — Product Requirements

One line: what this is and who it's for.

## The Core Journey
The complete path, end to end — arrival, first use, the core loop, what counts as success.
Numbered steps in plain language, concrete enough that a stranger could follow along.
This is the spine of the document; everything below elaborates on it.

## Features and Behavior

<!-- Structure this to fit the product. If it genuinely has several distinct areas of
     functionality, group them under descriptive headings (### Finding recipes, etc.).
     If it's one surface and one loop, keep it flat and just describe the behavior. -->

### [Area of functionality, or drop this level entirely]

What the user can do here, and what they see. Be specific about the things that make
this product *this* product rather than a generic version of its category.

<!-- OPTIONAL: user stories with acceptance criteria. Use them where they add precision
     — multiple user types, several distinct capabilities, a journey with branches. Skip
     them for a single-user, single-surface tool and describe the behavior directly. -->

- As a [specific person], I want [capability] so that [benefit].
  - [ ] Acceptance criterion — verifiable through observable behavior or output
  - [ ] Acceptance criterion

## States and Boundaries

<!-- Include ONLY the ones that apply to this product. Candidates: first use, normal
     use, empty state, error states, success state, what persists between sessions,
     what disappears, permissions and boundaries (who can see or do what), and
     assumptions hidden inside the core interaction. A product that stores nothing
     gets no persistence entry. Do not list a state just to fill the section. -->

- **[State]** — what the user sees and what happens.

## Decisions I Made For You

<!-- Every detail the agent chose on the learner's behalf, so it's visible and easy to
     overturn. Expected to be non-empty. One line each: the choice, and why it was safe
     to make without asking. -->

- [Choice] — [why this was conventional / reversible / low-impact].

## What We're Building
Everything the proof of concept must do to be complete.

## Deferred From the POC
Features this product implies but is not building now — the account system behind
"my saved items", the sharing behind "send it to a friend". Name each one and say why
it's out for now, so none of them slip into the build unnoticed.

## Possible Later Enhancements
A sentence or two each. No acceptance criteria. Still on the table for later.

## Non-Goals
Specific things this project will NOT do, each with a brief reason.
Pull from what scope cut, plus anything that will tempt during the build.

## Open Questions
Unresolved items. Flag whether each must be answered before `4-spec` or can wait.
