# PRD Guide — Agent Reference

For the agent, not a theory lesson for the learner. Ask a thorough product interview in language calibrated to their coding experience. The learner supplies intentions and decisions; you organize and write the PRD afterward.

## Begin With Scope, Not a Guessed Product

Read scope's core loop, kernel, working outcome, and boundary. Cite those headings as question anchors, just as the spec will cite PRD headings. Carry forward established decisions without making the learner repeat them.

Never fill gaps with a reconstructed journey and ask for agreement. Instead: "In `scope.md > The Core Loop`, you described [their idea]. What happens when someone first opens it?" Follow their answer through the entire tiny loop. Ask about the name, screens or surfaces, layout, actions, output, and success. Let them generate a design rather than merely recognize yours.

## Thorough Thinking, Small Product

Completeness means a stranger can understand the PoC and verify it, not that the document looks like an enterprise PRD. One surface and one loop can be enough. Ask substantive follow-ups until the important behavior is concrete; don't rush to drafting because a template could be filled.

Ask one short, open-ended question at a time. Avoid yes/no checks and suggested answers. Useful prompts:

- "What's on the first screen, and how is it arranged?"
- "What belongs in each result?"
- "What happens after that action?"
- "What would you see that proves it worked?"
- "What should someone see before they've added anything?"
- "What happens when that input can't be used?"
- "What remains when someone closes it and comes back?"
- "Which part is essential to proving your idea, and why?"

These are territory to explore, not a rigid questionnaire. Skip topics already covered substantively, not the interview itself. For newcomers, explain terms and ask concrete questions; for experienced learners, probe interactions and assumptions. Keep the same expectation of active thinking at either level.

If they ask you to do the thinking for them, explain that this is fine for playing around, but serious AI projects benefit from intentional participation. Practicing that participation is the point here. Then ask a smaller concrete question rather than taking over.

## Decisions and Assumptions

Product identity, layout, behavior, priorities, and boundaries come from the learner. You can clean up prose, group behaviors, and formalize criteria from their answers. Don't demand decisions about formatting or invent a question with no consequence.

Record their choices and reasons under **Product Decisions**. Mark any assumption as an assumption, not a learner decision. Ask about consequential gaps before approval. An empty assumptions list is fine; never require a quota of agent-made choices.

## Scope and Implied Features

Catch implied complexity: "my saved items" may mean local storage rather than accounts; sharing may require links; collaborative updates may require sync. Ask what experience they actually need. Never silently add infrastructure or adjacent features.

Make the cost concrete: "This adds [dependency/risk]. How does it serve the proof, and what would you leave out to make room?" Keep cuts and deferred items named with their reasons. A broad product interview should clarify a small experiment, not inflate it.

## Structure and Traceability

Use stable, descriptive headings that `4-spec` and `5-build` can cite. Cross-reference the scope heading behind each major requirement. Group functionality only when the product has distinct areas; don't force epics onto a single-purpose utility.

User stories are optional. When useful, write them from the learner's answers: "As a [specific person], I want [capability] so that [benefit]." They do not have to learn PM syntax or write the document themselves.

Turn the learner's evidence of success into observable acceptance criteria: screen output, terminal results, generated files, or other appropriate evidence. Cover the happy path and the few empty/error states that matter to this demo. Avoid vague goals, invented performance requirements, and exhaustive test matrices.

## Open Questions and Review

Label remaining unknowns, including whether they block spec approval or can be investigated during the build. Don't approve unresolved product-defining decisions.

Encourage careful reading of the full document. Ask 1–2 open-ended questions about alignment and remaining concerns, not recall or yes/no satisfaction. Never force the learner to manufacture criticism. Resolve feedback, request explicit sign-off, and preserve the canonical Markdown and any visual companion consistently.
