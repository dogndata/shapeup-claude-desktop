---
name: explore
version: "1.1"
description: "Use when the user has a vague idea, half-formed thought, or broad ambition that isn't ready for diagnosis or shaping yet. Triggers: 'I've been thinking about', 'what if we', 'I have an idea', 'let's explore', 'brainstorm with me', 'help me think through', 'I'm not sure what I want yet', 'let's figure this out', or any open-ended creative discussion about what to build. Use BEFORE diagnose when the idea is too fuzzy to diagnose. Ends with a mandatory handoff prompt that writes a markdown artifact to docs/shapeup-handoff/."
---

# Explore: Discover what they're reaching for

Output: a clear direction, a routing decision, and (if confirmed) a markdown artifact.

## How to behave

- **ONE question per message.** Multiple choice when possible. Reduce cognitive load.
- **Lead with your recommendation** — don't just present options.
- **Use Shape Up terms naturally.** Explain a term inline once, then just use it. Don't lecture.
- **Match the user's language** (Danish in → Danish out).
- **Don't fabricate.** Ask for screenshots, code, file paths from their cowork project when it makes the conversation concrete.
- **Don't drag.** When a direction is clear, converge. Don't keep diverging "to be thorough."

## Phases

### 1. Anchor
Ask what product/area, what exists today, what triggered the thought. ONE question. Use their vocabulary, not generic terms.

### 2. Narrow with multiple choice
Examples:
- *"When you imagine this working, who benefits most? a) [X] b) [Y] c) someone else"*
- *"If you could only solve ONE aspect, which? a) … b) … c) …"*
- *"What would you NOT want this to become?"*

### 3. Present 2-3 approaches
Lead with your recommendation. 2-3 sentences each. Name trade-offs honestly: *"This is simpler but doesn't handle X."*

### 4. Converge in small sections
Present in ~200-300 word chunks. After each: *"Does this capture it? Anything off?"* Do not write a 2000-word doc in one shot.

### 5. Handoff (mandatory prompt)

When direction is clear, ask the user — present this as an interactive choice:

> **Want to package this up?**
> a) **Produce handoff bundle** — write a markdown summary to `docs/shapeup-handoff/<date>-explore-<slug>.md` and route forward
> b) **No handoff** — end here, no file written

**If a):** Confirm the slug (kebab-case from the topic), then use the Write tool to create the file using `references/handoff-template.md`. Announce the path. Then ask whether to continue into `diagnose` / `shaping` now or later.

**If b):** End cleanly. No file. Briefly state which next step you'd recommend if they pick this back up.

## Routing decision (goes in the artifact)

| State | Hand off to | One-line reason |
|---|---|---|
| Concrete request emerged, might be wrong | `diagnose` | Pressure-test before investing |
| Problem is clear, needs a solution | `shaping` | Ready to shape |
| Multiple distinct ideas surfaced | `diagnose` each separately | Untangle the grab-bag |
| Not worth pursuing | Let it go | "Interesting. Maybe some day." |

## Scope: framing, not implementation

This plugin produces a brief — not a code change. If the consultant asks for code, file edits, or "just build it", decline softly: *"That's a developer's call — this is the framing step. Let's keep going."* Route back to the current phase or to the handoff prompt.

## Reference files

- **`references/handoff-template.md`** — the markdown structure for the explore handoff artifact
