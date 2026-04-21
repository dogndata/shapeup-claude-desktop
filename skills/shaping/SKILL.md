---
name: shaping
version: "1.0"
description: "This skill should be used when the user wants to shape work, write a pitch, scope a feature, define a project appetite, evaluate whether a feature request is ready for development, turn a raw idea or customer request into shaped work, identify rabbit holes, create a parts/mechanisms table, breadboard a solution, perform an R x F fit check, or ask how to shape something. If the request seems problematic or poorly defined, consider using shapeup:diagnose first. Covers the full Shape Up shaping methodology: setting boundaries, finding the elements, addressing risks, and writing the pitch document."
---

# Shaping Work (Shape Up Methodology)

## Overview

Shaping is the pre-development work of defining what to build before handing it to a team. Raw ideas and customer requests are not ready for development — they need to be shaped into something with clear boundaries, a defined solution approach, and identified risks.

Shaping sits between the abstract (a raw request) and the concrete (a detailed spec). Shaped work has three required properties:

1. **Rough** — Unfinished on purpose. No wireframes, no pixel-level detail. The building team has creative room.
2. **Solved** — The main elements are thought through. Open questions are answered. It's not just a description of the problem.
3. **Bounded** — The appetite is set, no-gos are explicit, and rabbit holes are patched. The team knows where to stop.

## Teaching Approach

This is where the richest learning happens — breadboarding, appetite, parts/mechanisms. Claude co-creates artifacts through dialogue, not dictation. Don't dump the full Phase 1–4 process on the user. Guide them through it step by step, introducing each phase as a natural next question.

**For appetite:** "Before we design a solution — how much time is this problem *worth*? Not how long it'll take, but how much you'd invest. Shape Up calls this the *appetite*. Is this a one-week thing or a six-week thing? That changes what kind of solution makes sense."

**For breadboarding:** "Let's map out what happens. Where does the user start? What do they see? What can they do there? — in Shape Up, those are called *Places*, *Affordances*, and *Connections*. Let's build this together."

**For parts/mechanisms:** "Let's list the moving pieces. Each part of the solution gets a name and a description of how it works. Think of it as a bill of materials."

## Grounding in the User's Product

You don't have access to the codebase or UI. Shaping is done through the user's description of the current product and the user's sense of how it should change.

- **Before Phase 2 (Find the Elements), walk through the current product with the user.** "Describe the screen/flow as it exists today. What does the user see? What can they do?"
- **Use screenshots when the user can share them.** Real images turn breadboarding from speculation into modification.
- **Build breadboards from their descriptions.** Don't invent Places and Affordances — derive them from what the user tells you exists.
- **All technical claims must be marked as unvalidated.** This plugin is for non-technical users; the pitch's `Confidence: First-pass shape — needs technical review` field is mandatory.

## Co-Creation Scaffolding

Walk through breadboarding as a conversation, not a template-filling exercise. Ask one element at a time and build the breadboard incrementally, showing progress after each answer.

1. **Start with place:** "Where does the user start? What screen or page are they on?"
2. **Discover affordances:** "What can they do there? What do they see and interact with?"
3. **Follow connections:** "What happens when they do that? Where do they end up?"
4. **Show progress:** After each answer, write the breadboard notation and show it back: "OK so our breadboard looks like this now: ..."
5. **Iterate:** "What's missing? What else can they do here?"

For non-technical users, use their language first, then map to Shape Up terms: "OK so they click 'Send' and it goes to a confirmation screen — in our breadboard, that's a Connection from the Send affordance to a new Place called Confirmation."

## Confidence Marking

When non-technical users shape work, the pitch should clearly signal what needs technical validation. The pitch output includes metadata like:

- **Shaped by:** [Name], with Claude
- **Confidence:** Needs technical feasibility review

Confidence levels:
- **First-pass shape — needs technical review** — Shaped without engineer input. Solution approach is reasonable but unvalidated.
- **Technically validated** — A senior engineer has reviewed and confirmed feasibility within the appetite.
- **Ready for betting** — Fully shaped, technically validated, risks patched.

## Danish Context

This skill is used in a Danish work environment. Users may write in Danish and domain terms may be in Danish. Respond in the same language the user writes in. When working with Danish-language products or workflows, use the Danish terms naturally alongside Shape Up methodology terms.

## When to Shape

Shape work when any of these are true:
- A raw customer request or feature idea exists without a clear solution approach
- Someone has proposed a solution without properly identifying the underlying problem
- A piece of work has no defined time boundary (appetite)
- There are unanswered technical or design questions that could derail building
- A "grab-bag" project exists (e.g. "redesign X" or "X 2.0") without a clear definition of done

## The Shaping Process

Follow these four phases in order. Each phase produces concrete artifacts.

### Phase 1: Set Boundaries

Define the appetite and clarify the raw idea.

1. **Identify the raw idea** — What is the request? Who asked for it? What triggered it? Default response to raw ideas: "Interesting. Maybe some day." — do not commit prematurely.
2. **Narrow the problem** — Separate the underlying problem from proposed solutions. Ask: "When did you first want this? What were you doing at that moment?" Probe for the triggering workflow, not features.
3. **Set the appetite** — How much time is this worth? Small Batch (1-2 weeks) or Big Batch (6 weeks)? The appetite is NOT an estimate — it is a deliberate constraint that changes the *kind* of solution, not just the scope.
4. **Define what's out** — Explicitly state what is NOT included. Watch for grab-bags ("redesign X", "X 2.0") — decompose into problem-driven sub-projects.

**Output:** A clear problem statement, appetite, and explicit boundaries.

For extended guidance on narrowing problems, setting appetite, and finding the nugget of value, consult `references/shaping-process.md`.

### Phase 2: Find the Elements

Sketch a solution at the right level of abstraction — not wireframes, not code.

1. **Move fast, be concrete** — Work in the "breadboard" level: name the key places, affordances, and connections. No visual design.
2. **Create a Parts/Mechanisms table** — List each part of the solution (F1, F2, ...) with its mechanism (how it works). This is the "bill of materials."
3. **Breadboard the flow** — Map Places (screens/dialogs), Affordances (things users interact with), and Connections (how they flow). Breadboarding is a *debate engine*: drawing the flow surfaces hidden questions and forces decisions.
4. **Stay at the right abstraction** — Name components and behaviors, not pixel-level details. The team decides visual design. At this stage, there is no commitment — the shape can still be abandoned ("no conveyor belt").

**Output:** Parts/Mechanisms table and breadboard description.

Consult `references/artifacts-guide.md` for detailed examples and formats.

### Phase 3: Address Risks & Rabbit Holes

Stress-test the shape before committing to build it.

1. **Assess the risk profile** — Well-shaped work has a **thin tail** (might take a few days extra but won't balloon). Poorly shaped work has a **fat tail** (could consume multiples of the appetite). The goal of de-risking is to make the tail thin.
2. **R x F Fit Check** — Cross-check every known requirement against the shape. For each requirement, mark: Core goal / Must-have / Out / Undecided. Check whether the shape satisfies it (pass/fail).
3. **Identify rabbit holes** — What technical unknowns could blow up the timeline? Call them out explicitly.
4. **Patch holes with concrete solutions** — Do not just flag risks — provide specific, even compromised, solutions. The shaper makes pragmatic trade-offs that a team under deadline pressure cannot easily make.
5. **Present to a technical expert** — Before writing the pitch, walk a senior engineer through the concept. Ask: "Is this possible within the appetite?" — not just "is this possible?"

**Output:** R x F Fit Check matrix, list of rabbit holes with declared boundaries.

### Phase 4: Write the Pitch

Assemble everything into a pitch document — the final shaped work artifact.

Follow the format in `references/pitch-template.md`. A pitch contains:

1. **Problem** — A single specific story showing why the status quo doesn't work. This story is the *fitness test* for the solution — people judge whether the solution makes this story better.
2. **Appetite** — Time budget (Small Batch or Big Batch) and why
3. **Solution** — Parts/Mechanisms table and breadboard (from Phase 2). For "linchpin" parts, selectively add embedded fat-marker sketches to help readers see the concept without over-specifying.
4. **Rabbit Holes** — Known risks and how they're bounded (from Phase 3)
5. **No-Gos** — Explicit list of what is NOT in scope

## Working with Raw Requests

When a request feels off, seems too simple, or smells like a symptom rather than the real problem — use `shapeup:diagnose` first. It applies five diagnostic lenses (symptom vs disease, scope boundaries, solution-as-problem, process vs software, unsurfaced assumptions) to find the root cause before you invest time shaping.

When presented with raw customer requests or feature ideas:

1. **Default response: "Interesting. Maybe some day."** Do not commit. Do not show too much enthusiasm. Preserve optionality.
2. **Do not accept proposed solutions at face value.** Dig for the underlying problem. Ask about the triggering moment and broken workflow.
3. **Question time estimates from non-technical staff.** They lack context on implementation complexity.
4. **Separate "nice to have" from the core pain.** Focus shaping on the real problem.
5. **Watch for grab-bags.** Vague scopes like "redesign the Files section" or anything labeled "2.0" fail because there is no clear definition of done. Decompose into problem-driven sub-projects with individual appetites.
6. **Look for the "one thing" that would make the biggest difference.** Not everything needs to be shaped — some requests are better addressed by simplifying or combining.
7. **Compare to baseline, not ideal.** The standard is "better than what customers have today" — not perfect.

## After Shaping

Once a pitch is approved:
- Break the solution into **vertical slices** (V1, V2, ...) — each delivers working functionality
- Each slice should be independently demoable
- Use `playbook:select-formation` to choose the right agent orchestration pattern
- Use `playbook:decompose` to break into agent-ready task groups
- If the solution approach needs further exploration, step back to `shapeup:explore`

## Key Principles

- **Fixed time, variable scope** — The appetite is a hard constraint. Scope adjusts to fit.
- **Rough, solved, bounded** — Shaped work must have all three properties. Rough (room for the team), solved (main elements defined), bounded (appetite set, risks patched).
- **Shaped, not specified** — Leave room for the building team to make decisions.
- **No backlogs** — If it's important, shape it. If it's not worth shaping, let it go. Important ideas come back naturally.
- **Uphill vs. downhill** — Unknowns are uphill (risky). Solved problems are downhill (execution). Shape until everything is downhill.
- **Appetite, not estimate** — "How much time is this worth?" not "How long will this take?" The appetite changes the *kind* of solution.
- **Circuit breaker** — Work that exceeds the appetite is cancelled by default, not extended. Shaping must be honest about fit.
- **Thin tail, not fat tail** — Well-shaped work has predictable risk. Poorly shaped work can balloon without limit.

## Reference Files

- **`references/shaping-process.md`** — Detailed walkthrough of each phase with extended examples
- **`references/pitch-template.md`** — Template for writing pitch documents
- **`references/artifacts-guide.md`** — How to create Parts/Mechanisms tables, breadboards, and R x F Fit Check matrices
- **`references/glossary.md`** — Complete Shape Up terminology reference
