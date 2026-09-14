---
doc: spec
status: draft
---
<!-- `status` is the progress state every skill reads. Write `draft` when you first save this file,
     and change it to `approved` only when the learner explicitly signs off. Never skip the draft save —
     an unsaved draft dies with the conversation. -->

<!-- Adaptive template. Drop any section that doesn't apply to this product, add any
     section it needs, and let the nesting depth follow the product's real complexity —
     a single-file tool needs two levels, a multi-surface app might need four. Empty
     headings added for symmetry make the spec worse. The one rule: anything
     `5-build` will point at needs its own heading.

     Write the plain-language sections so the learner can read them back to someone
     else. That is the test this document has to pass. -->

# [Project Name] — Technical Spec

## How This Works, In Plain Language
The pieces of the system and what each one does, in the learner's vocabulary — no
term used here that wasn't explained in the conversation.
Why this shape rather than something more elaborate.
Written so the learner could read this section aloud and have someone understand
their app.

## The Core Journey Through the System
The PRD's Core Journey, traced step by step through the pieces above.
"The user does X → that goes here → this happens → they see Y."
PRD ref: `prd.md > The Core Journey`.
This is the section that makes the architecture explorable rather than abstract.

## Stack
Language, framework, key libraries, with versions where they matter.
Documentation link for each major dependency.
One line of rationale per choice.
Anything unverified: say so plainly and flag it to check early in the build.

## Where It Runs and How Someone Tries It
Runtime (browser, local process, server, command line) and environment requirements
(language version, API keys needed).
How another person experiences it: local demo, deployed URL, or a recording. If
deployed, the target platform and the deploy steps.

## Look and Feel
<!-- The design direction carried forward from `scope.md > Inspiration & Identity`, in
     terms a build agent can act on. Direction, not a full design system — and keep it
     proportional: a CLI tool's entry is one line about output formatting and tone. -->
Palette or color feeling. Typography character. Density and energy — spacious and calm,
or dense and fast. The tone of the interface copy. Named references worth drawing from.
Must be consistent with the Stack above: if the stack constrains styling, say plainly what
it can and cannot honor here.

## Components

<!-- Group at whatever depth fits. Each component: what it does, how it connects,
     which PRD heading it serves. -->

### [Component]
What it does. What it talks to.
PRD ref: `prd.md > [heading name]`.

## Data Model
Schema, relationships, or state shape — whatever fits the stack.
For each piece of data: where it lives, how it gets updated, and what happens when
the user leaves and comes back.

## File Structure
Full ASCII tree, every file and folder annotated with its purpose.

```
project/
├── src/
│   └── ...
├── devpost/        # Devpost learning workspace
└── ...
```

## External Services and Dependencies
Everything outside the codebase: APIs, databases, hosting.
For each: the exact calls (endpoint, payload, response), documentation link, keys
required, rate limits, and cost.

## Important Failure Modes
The two or three places this will realistically break, each with its chosen fallback.
Not exhaustive error handling.

- **[What breaks]** → [what the user sees instead].

## What Was Simplified and Why
<!-- The substitutions made to keep the POC coherent. This is engineering judgment
     on the page, not a list of shortcomings — expected to be non-empty. -->

- **[Simpler thing built]** instead of [fuller thing] — [why]. The fuller version
  would [what it would take].

## Decisions and Open Issues
Decisions made here, each with what was chosen, why, and the tradeoff accepted —
including the ones made on the learner's behalf, named as such.
Then anything still unresolved: ambiguities from the self-review, and open questions
carried over from `prd.md > Open Questions`.
