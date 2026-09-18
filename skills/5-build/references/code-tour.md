# Five-Minute Code Tour — Agent Reference

One guided route through the finished code, then a reusable app map. This happens after build revisions in both modes and before submission chores. It is not an architecture exam or an extra product feature.

## Prepare From the Actual Code

Read the current implementation, not just the planned file tree. Pick one core action with a visible result and trace it through 2–3 meaningful code locations. These may be functions in the same file; never invent layers for a tiny CLI or single-file app. Use the learner's experience to set explanation depth.

Prepare a short route and one safe, incidental edit that does not change the kernel, require credentials, delete data, or add dependencies. A label, display detail, or harmless default can work. Don't add logging infrastructure, a debugger setup, or an in-app tutorial just for this tour.

## Guide the Tour — About Five Minutes Total

1. **Why and setup (~30 seconds).** Use the skill's brief cognitive-debt explanation. Frame this as a useful investment in ownership, not a claim that AI damages the brain. Have them open the project in their IDE or editor and run the app using its documented command.
2. **Follow one action (~2 minutes).** Use a core behavior they've already tried, or a different action if they express curiosity. Have them perform it, then guide them to 2–3 locations in execution order: the input/entry point, the important logic or storage if present, and the result/output. At each stop, give the exact relative path and function/symbol or searchable snippet, with current line numbers only as a convenience. Explain in one or two sentences how that code connects to the visible behavior. Let them navigate; don't just dump excerpts into chat. Group navigation instructions naturally, without requiring approval at every stop.
3. **One optional edit (~1 minute).** Invite them to make the prepared tiny change themselves and predict the visible effect, conversationally—not as a graded question. Give the exact location and enough help for their experience. Let them rerun or refresh and see what happened. If they decline, record that and move on without a replacement exercise. If they get stuck, show the change rather than grilling them. Verify a kept change and commit it; don't overwrite unrelated edits or silently undo their work. Update planning docs only if the retained change affects a documented decision.
4. **Reveal the map (~1 minute).** Show the finished `devpost/app-map.html` and explain how to open it again. It preserves the route and useful places to make future changes. No recall test or separate approval ceremony. Record completion after the learner has actually followed the tour, not merely after sending instructions.

Keep remaining time for navigation friction. If running the app or opening an editor isn't possible, say so and use real source excerpts and an explicitly static walkthrough of the same route. Never claim to have observed execution just because the code suggests a path. Don't force a setup detour or pretend the learner made an edit. If the session is interrupted, record where it stopped and resume there.

## The App Map

Generate a standalone `devpost/app-map.html`, regardless of the planning review-format preference. It is **not an HTML build checklist** and does not require adding a page to the learner's app. Use actual post-revision, post-edit code, not an aspirational architecture.

Include:
- A plain-language overview of what the app does and its few main pieces.
- A small inline SVG or HTML/CSS diagram connecting the tour's action, code locations, and visible result. Show storage or external services only if they exist.
- The 2–3 tour stops in order, each with the real relative path, stable symbol/search anchor, and a brief explanation. Don't depend on local-editor deep links working.
- A few concrete **“To change this, start here”** pointers grounded in the current code, including the tiny edit if taken. No exhaustive file tree or code dump.
- How to run it again, plus the source commit used for the map when available; explain that the map is a snapshot and can drift after future changes.

Keep it readable and keyboard-accessible, with optional native `<details>` reveals. No build step, framework, CDN, network dependency, analytics, or secrets. Essential content must work with scripts disabled. Escape code snippets so source text cannot become executable HTML. Don't embed learner-profile details or private sample data; the repository will be public.

Open/check the artifact where tools allow, check all paths and anchors against the actual source, and confirm it remains useful offline. Be honest about any browser checks you cannot perform. Record its path in the checklist and commit the map and tour record. If later shipping fixes affect the mapped route, refresh the map without repeating the learner tour.
