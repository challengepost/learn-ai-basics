# PRD Guide — Agent Reference

This document is for the agent only. It informs how you run the `3-prd` conversation and write the PRD. Do not surface PM jargon, framework names, or theory to the learner. Use this knowledge to ask better questions and produce a more rigorous document.

## What Makes a Good PRD Here

The scope doc is a sketch of the heart of the idea. The PRD is the complete product definition: the journey is fully described, the features and behavior are specific, and nothing consequential is left unresolved. **Completeness is the standard, not length** — a short PRD for a small product is correct, and padding a one-surface utility to look impressive is a failure. It's done when a stranger could read it and know what to build and what "done" looks like.

The other half of the standard: the learner must not have had to behave like a professional product manager to get there. You draft; they decide the things that matter.

## Reconstructing the Core Journey

This is your opening move, before you ask the learner anything. Read the scope and write the whole journey end to end — arrival, first use, the core loop, whatever counts as success. Where scope is silent, fill it in with your best guess and *mark the guess*. Then hand the reconstruction over to be reacted to.

Why this beats asking: an open question ("what should happen on first launch?") makes the learner generate a design from nothing — the hard version of the task, and the one they're least equipped for. A concrete wrong draft asks them only to *recognize*, which is fast and produces sharper information. "No, not a list, it should be one card at a time" produces more useful information than a string of open questions.

The failure mode is presenting the reconstruction as finished. Present it as a first pass with visible guesses, and say plainly that you expect to be wrong in places.

## The Decision Rule

The most important judgment in this skill. Every gap you find gets sorted one of two ways.

**Ask the learner** when the detail:
- changes the product's promise or the core journey;
- expresses product identity or taste;
- touches a priority, constraint, or concern the learner already said matters;
- adds meaningful scope, cost, or risk;
- would make the product feel wrong if guessed.

**Decide it yourself** when the detail is conventional, reversible, low-impact, and easy to change later.

Worked, using a tool that turns rough voice notes into a clear action brief:

| Gap | Call | Why |
| --- | --- | --- |
| What a useful finished brief contains | Ask | It *is* the promise |
| Checklist vs. narrative summary | Ask | Taste; sets the product's voice |
| Whether saved briefs are browsable | Ask | Adds another meaningful product surface |
| Whether a brief is private or shareable | Ask | Guess wrong and the product is wrong |
| Notes go into one input | Decide | Conventional; trivially changed |
| Brief appears below the input | Decide | Layout, reversible |
| Saved briefs sort newest-first | Decide | The obvious default |
| Button labels and empty-state wording | Decide | Low impact, easy to overturn |

Both failure modes are real. Asking about everything turns the learner into a PM filling out a form and overwhelms them with irrelevant decisions. Asking about nothing produces a generic product wearing their idea's name. Default to deciding conventional details yourself; ask only when the answer has a real downstream effect. When the learner profile names an area they want ownership of, move that area's borderline calls to the "ask" side.

## Making Your Decisions Visible

Every call you made on the learner's behalf goes in the PRD, marked as yours. The list is expected to be non-empty — if it's empty you either asked too much or hid something.

A polished document that reads as though the learner decided all of it is a failure, because it removes their ability to notice and overturn an inference. Visibility costs one line per decision. A short review of named choices is cheap; discovering the wrong one mid-build is not.

## Implied Features

Products imply features nobody discussed: "my saved items" implies accounts, or at least identity and storage; "send it to a friend" implies sharing and links; "it remembers my preferences" implies settings and persistence; "see what everyone else added" implies multi-user and sync.

Catch them, name them to the learner, and put them in the deferred section with a reason. Never let one enter the POC silently, and never let one enter by accident because a requirement's wording assumed it.

## Structure That Fits the Product

Use epics — named groups of related functionality — only when the product genuinely has several distinct areas. A recipe app plausibly has *Finding recipes*, *Managing ingredients*, and *Cooking flow*. A single-purpose batch file renamer has one area, and forcing three epic headings onto it obscures a simple product rather than clarifying it; keep that structure flat and describe the behavior directly.

Either way: **headings must be stable and descriptive**, because `3-prd` and `5-build` reference them by name — "this module implements `prd.md > Finding Recipes`". Traceability is the requirement; epic ceremony is not.

## User Stories

Stories are a precision tool, not a required format. **They help** when there are multiple kinds of user, several distinct capabilities, or a journey with real branches — anywhere "who wants this and why" is doing work. **They're overhead** when there's one user, one surface, one loop; describing the behavior directly is clearer.

Where you use them, the format is simple and accessible to anyone:

**"As a [specific person], I want [thing I can do] so that [why it matters to me]."**

What makes a good story:
- The person is specific enough to picture ("a first-time visitor", not "a user")
- The capability describes what they want to accomplish, not how the UI works ("find recipes that use what I have", not "click a dropdown menu")
- The benefit explains real-world value ("so I don't waste food", not "so the feature works")

Common mistakes to watch for and gently redirect:
- Too vague: "I want the app to work well" — push for specifics
- Prescribing UI: "I want a sidebar with filters" — redirect to the need behind it
- Missing the "so that": stories without benefits are tasks, not stories
- Too big: "I want to manage my account" — break it into specific capabilities

Never make the learner write stories. You write them from what they said; they confirm the meaning is right.

## Acceptance Criteria

Also a precision tool. Write criteria for the things whose "done" is genuinely ambiguous, or that `5-build` will need to verify. Skip them where the behavior is self-evidently either working or not. Criteria must be verifiable through observable behavior or output—a screen, terminal result, generated file, or other product-appropriate evidence.

Good:
- [ ] When I search for "chicken", recipes with chicken appear
- [ ] If I have no ingredients saved, the app shows a helpful empty state
- [ ] Clicking a recipe shows the full ingredient list and steps

Avoid: vague criteria ("the search works well"), implementation-specific criteria ("the SQL query returns results in < 100ms"), and untestable criteria ("the UX is intuitive"). Cover the happy path first, then the empty and failing cases that actually apply.

## Asking Sharpening Questions

The core technique is translating vague intentions into precise behavior. Useful patterns:

**Zooming in:** "You said users can browse recipes. What do they see first? A list? Cards? How are they sorted?"

**Surfacing assumptions:** "You're assuming people will add their ingredients. But what does the app look like before they've added anything? What's the very first thing a new user sees?"

**Finding contradictions:** "You want it to be simple, but you also want filtering by cuisine, diet, and cook time. Which matters most if you had to pick one?"

**Testing completeness:** "Walk me through this from start to finish. You open the app. Then what? What do you tap first? What happens next?"

**Probing the edges:** "What if someone searches and there are no results? What if they have only one ingredient? What if they have fifty?"

Calibrate against the learner profile rather than a fixed experience level:
- Where **Vocabulary and Concepts Likely to Need Explanation** is long, aim for 2-3 eye-opening "what if" moments and no more — the lesson is that planning pays, not that products are infinitely complicated.
- Where the profile shows fluent building experience, push on the interactions *between* features, which is where they're most likely to have hand-waved.
- Where the profile shows deep experience, they'll anticipate the edges themselves; your value is making implicit decisions explicit and on the page.
- Where **Areas Where the Learner Wants Ownership** names something, ask rather than decide, even for borderline calls.

## Scope Guarding

Be exhaustive about what's IN without letting the proof of concept lose its focus. Watch for:
- Requirements that keep spawning sub-requirements
- "While we're at it" additions
- Features that add substantial complexity without strengthening the demonstration
- Vague requirements hiding enormous complexity ("social features," "real-time sync," "recommendations")

Name creep the moment you see it: "This is growing. Essential to the thing you're proving, or something we add later?" Explain the added cost, dependency, risk, or maintenance burden without inventing a duration. Make the case; the learner chooses.

## Non-Goals

Strong non-goals prevent creep during the build. Make them specific and named — "we are NOT building user profiles, because the app works fine with anonymous, session-based use" beats "no extra features." Pull them from two sources: what scope already cut, and adjacent features that will tempt the learner mid-build.

## Open Questions

Some things won't resolve in this conversation, and that's fine. Name them so they don't become surprise roadblocks. Flag whether each must be answered before `3-prd` or can wait until the build.
