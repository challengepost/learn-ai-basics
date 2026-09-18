---
doc: checklist
status: draft
---
<!-- `status` is the progress state every skill reads. Write `draft` when you first save this file,
     and change it to `approved` when the learner clearly approves the displayed plan ("looks good" counts).
     Do not request a second sign-off. Never skip the draft save —
     an unsaved draft dies with the conversation. -->

<!-- Progress state for `5-build`. `5-build` reads this file to find the next
     unchecked slice, and rewrites it as it goes — ticking boxes and appending to
     Revisions. Every slice MUST carry the same fields in the same order so parsing
     stays reliable. `Learner check:` gives the learner a plain-language way to
     try the completed behavior in learn mode and at fast-mode checkpoints.
     Keep this checklist in Markdown only, regardless of Review Format.

     Internally, a slice is a thin end-to-end increment that makes a real part of the product
     usable, never a lone layer like "build the data model". Slice 1 includes project
     bootstrapping — scaffold, dependencies, config — as part of delivering its first
     real behavior. The examples below show the format; replace them entirely. -->

# Build Checklist

## Slices

- [ ] **1. You can type an entry and see it appear in the list**
  Becomes usable: A running app where an entry typed into the form shows up on screen in the list. Nothing persists yet.
  Why now: Proves the whole path end to end on the first slice — scaffold, form, state, render — so every later slice has somewhere to land.
  PRD ref: `prd.md > The Core Journey` (steps 1-3)
  Spec ref: `spec.md > Components`, `spec.md > File Structure`
  Build: Scaffold the project per the spec's file structure, install dependencies, add the entry form and the in-memory entry list, render entries newest-first.
  Verify (mechanical): Run the dev server and confirm it starts with no errors; submit an entry and confirm it renders in the list.
  Learner check: Open the app, add an entry, and say whether it looks and feels the way you pictured it.
  Commit: `Add entry form and live list`

- [ ] **2. Entries survive a restart**
  Becomes usable: Entries written before closing the app are still there when it reopens.
  Why now: Persistence is the first place the data model can be wrong, and finding that out now is cheap.
  PRD ref: `prd.md > States and Boundaries` (what persists between sessions)
  Spec ref: `spec.md > Data Model`
  Build: Add the storage described in the spec, write on submit, load on startup, leave the render path unchanged.
  Verify (mechanical): Add two entries, restart the server, reload, and confirm both load from storage.
  Learner check: Add an entry, restart the app, and confirm the entry is still in the list.
  Commit: `Persist entries to storage`

<!-- Continue for as many slices as the coherent POC requires.
     No target count. Each slice leaves the project working and committed, and the
     unique kernel appears early rather than last. -->

## Hands-on Checkpoints

<!-- Both modes require these three distinct learner pauses. Replace the timing notes
     with planned slice boundaries; don't add slices solely to reach a pause count.
     At each, the learner starts the dev server or equivalent, tries the app, and gives
     feedback. Check a box only after the learner reports back and issues are resolved. -->

- [ ] First usable behavior explored — [after which slice]
- [ ] Integrated core journey tried — [after which slice, or a separate pass for a tiny build]
- [ ] Final kick-the-tires exploration and feedback completed

## Final Review

<!-- Add agreed revision tasks as unchecked boxes here. Track findings and verification
     briefly so a fresh session can resume. No changes needed is a valid recorded result.
     Complete the box below only after all agreed revisions are verified, committed,
     retried by the learner, and they explicitly confirm readiness. -->

- [ ] Final review complete — feedback resolved and learner confirms ready to ship

## Code Tour and App Map

<!-- After final revisions, before submission. Both modes get one ~5-minute tour.
     Record progress so resuming never repeats completed stops. No extra approval gate. -->

- [ ] One action followed through 2–3 actual code locations with the learner
- [ ] One optional incidental edit offered — record tried/kept/reverted/declined
- [ ] `devpost/app-map.html` generated from finished code, checked, and shown

Route and stops: [action, real paths and symbols; completed stops if interrupted]
Edit outcome: [what happened, including declined; verification if changed]
Tour mode: [live app and editor, or explicit static fallback and why]

## Revisions

<!-- Leave this section empty when you write the checklist — no placeholder bullet.
     `5-build` appends a bullet here when implementation contradicts an assumption
     in the plan, in the form:

       - [What changed] — [what the build discovered that made the original plan wrong].

     One bullet per revision, no dates. This is how plan adaptation gets recorded,
     and it replaces any separate log. -->

