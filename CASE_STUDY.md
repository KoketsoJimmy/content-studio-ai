# Prompt Engineering Case Study: Improving Content Studio with Claude

## Summary

Content Studio started as a working single-file AI writing tool. The goal of this round was to turn it into a fuller "AI Content Workspace" without breaking what already worked. This case study looks at how the specification prompt was written, what it got right, where the scope outran a single response, and how the app's own "Improve my prompt" feature applies the same ideas.

## The challenge

Improving an existing application with an AI model has risks that building from scratch does not:

- The model may rewrite working code and silently drop features.
- A large wish list can produce shallow work on everything instead of solid work on the most important parts.
- Vague goals ("make it more modern") give no way to judge the result.

## Anatomy of the specification prompt

The full prompt is in [PROMPTS.md](PROMPTS.md). Its structure is worth reusing:

| Section | Purpose | Why it helped |
|---|---|---|
| Role statement | Sets the expertise to apply (frontend, UX, product, AI architecture) | Frames the kind of judgment expected |
| Numbered "Important rules" | Hard constraints: do not rebuild, preserve features, no new frameworks, no secrets in client code | Fences in the riskiest behaviors up front |
| Product vision | Describes the target workflow (Idea → Prompt → Generate → Edit → Refine → Repurpose → Compare → Finalize → Export) | Gives a single design test for every decision |
| Phased feature specs | Each feature has concrete behaviors, examples and "do not" notes | Makes results checkable rather than subjective |
| Named bug check | Points at specific suspected defects (`S.dirty`, duplicated refine controls, storage errors) | Directs attention to known weak spots |
| "Do not break" list | Enumerates existing features to preserve | Acts as a regression checklist |
| Priority order | Says what to build first if scope is too large | Turns an impossible request into a ranked one |
| Deliverable and summary format | Complete file plus a structured summary | Makes the output easy to review |

## What worked well

**1. Constraints before wishes.** Putting the preservation rules first made the work incremental. The changes were small, targeted edits to the existing file rather than a rewrite, which kept every existing feature intact.

**2. Specific bug hints.** Naming `S.dirty` and the refine controls led straight to real defects: form fields never marked the document as unsaved, and the refinement chips were added only after "Clear local preferences" (and duplicated on each reset).

**3. Explicit priorities.** The priority order made it clear which items to deliver first when the whole list could not fit in one pass.

**4. Behavior-level descriptions.** Examples such as the sample conversation turns ("Make it shorter", "Use the second hook") and the "Save & Continue / Discard Changes / Cancel" wording removed guesswork about the intended behavior.

## Where it fell short

**Scope versus capacity.** The prompt asked for 25 feature areas plus testing in one response. A response has finite room, so only the highest-priority subset was built: quick actions, Improve my prompt, selected-text refinement, stronger autosave and dirty-state handling, and the bug fixes. The rest is listed as a roadmap in the README. Lesson: a long wish list should be split into rounds, one deliverable each, with acceptance checks per round.

**"Test everything" without a test method.** The prompt asked for every feature to be tested but did not say how. In practice, verification was limited, and the changes should be tried in a browser. Lesson: specify how testing should happen (for example, a checklist the model fills in, or automated checks) and who runs it.

**Conflicting instructions need a tiebreaker.** "Return the complete file with nothing omitted" and "implement everything" pull against each other. The priority order resolved the conflict, which is why it was the most valuable section.

## Prompt engineering inside the app

The app applies the same principles to the prompts it sends to Claude. The "Improve my prompt" feature uses this instruction:

```
Rewrite the request below into a clearer, more specific brief for a <content type>.
Keep every fact the user gave; do not invent names, numbers or claims;
use [placeholders] for missing details.
Return only the improved request in 1-4 sentences, no quotes or commentary.
---
<user request>
---
```

Design choices:

- **Preserve facts, forbid invention.** This reduces hallucinated details.
- **Placeholders for gaps.** Missing details become visible `[placeholders]` instead of made-up content.
- **Strict output format.** "Only the improved request" keeps the result usable without cleanup.
- **Delimiters.** The `---` markers separate the instruction from the user's text.
- **User stays in control.** The result opens in a panel where the user can edit it, copy it, or keep the original.

## Practices to reuse

1. State hard constraints first and number them.
2. Describe desired behavior with examples, and name exact UI wording where it matters.
3. Point at suspected defects by name instead of asking for a generic "bug check".
4. Provide a regression list of features that must keep working.
5. Always include a priority order for large requests.
6. Plan the work in rounds and define how each round will be verified.
7. Separate instructions from the content to be processed, and treat pasted or fetched content as data, not instructions.

## Suggested next iteration

Split the remaining roadmap into small prompts, each with its own acceptance checklist, for example:

1. Version history with side-by-side comparison.
2. Repurposing hub (multi-format output cards).
3. Conversational mode with bounded context.
4. Projects and prompt library.
5. SEO assistant, quality analysis and extra export formats.
