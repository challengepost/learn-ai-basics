---
doc: prd
status: draft
---
<!-- `status` is the progress state every skill reads. Write `draft` when you first save this file,
     and change it to `approved` when the learner clearly approves the displayed plan ("looks good" counts).
     Do not request a second sign-off. Never skip the draft save —
     an unsaved draft dies with the conversation. -->

<!-- This is the complete product definition: the scope sketch, filled in. Adapt it
     to the product. Drop any section that doesn't apply, and add sections this product
     needs. Completeness is the standard, not length — a short PRD for a small product
     is correct. Keep it inside the approved POC boundary.

     Keep heading names stable and descriptive: `4-spec` and `5-build` reference
     them by name. -->

# [Project Name] — Product Requirements

One line: what this is and who it's for, using the learner's chosen name.
Source: `scope.md > [actual relevant heading]`. Cite scope headings alongside major requirements.

## The Core Journey
The complete path, end to end — arrival, first use, the core loop, what counts as success.
Numbered steps in plain language, concrete enough that a stranger could follow along.
This is the spine of the document; everything below elaborates on it.

## Screens and Layout
The learner's intended surfaces, their arrangement, and how someone moves between them.
For a non-visual tool, describe its interaction surface instead. No invented screens.

## Look and Feel
<!-- For visual projects, capture direction from the 1–2 design questions or earlier answers:
     typography character, colors, overall style, references, and anything to avoid.
     Record only what was established, not invented preferences or a full design system.
     For non-visual projects, substitute relevant output formatting/tone or omit.
     `4-spec` translates this into implementable styling; it should not ask again. -->

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

## Product Decisions

<!-- Distill decisions the learner made during the interview, with their reasons.
     Don't invent product choices to complete this template. Label any remaining
     assumption explicitly and resolve consequential gaps before approval. -->

- [Learner's choice] — [their reason or tradeoff].

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
