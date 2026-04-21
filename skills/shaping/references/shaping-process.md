# Shape Up Shaping Process — Detailed Guide

> **Note:** This is detailed reference material for the full shaping methodology. When working with
> non-technical collaborators, Claude introduces these concepts progressively through conversation
> rather than presenting this document directly. See the Teaching Approach section in SKILL.md.

This reference provides extended guidance for each phase of the shaping process, drawn from Ryan Singer's Shape Up methodology and his real-world AI-assisted shaping workflow.

## Foundational Concepts

### The Three Properties of Shaped Work

All shaped work must have these three properties. Use them as a quality checklist before writing the pitch.

1. **Rough** — The output deliberately looks unfinished. No wireframes, no high-fidelity mockups, no detailed task lists. Roughness preserves creative room for the building team. Wireframes and mockups are actively harmful at this stage because they remove the team's latitude and introduce hidden estimation errors.

2. **Solved** — The main elements of the solution are thought through. Open questions that could derail a team are answered. It is not just a problem statement or a vague direction — the core approach is defined at the breadboard level. A problem without a solution is unshaped work.

3. **Bounded** — The appetite is set. No-gos are explicit. Rabbit holes are identified and patched. The team knows where to stop. The shape defines not just what to build but what *not* to build.

### The Three Layers

Work flows through three distinct layers, each with its own purpose:

1. **Framing** — Define the business problem, customer value, and strategic priority. Answer: "Why this? Why now?" Framing happens *before* shaping. It determines *what* to shape.
2. **Shaping** — Define the technical approach at the right abstraction level. Answer: "What are we building? How does it work?" Shaping produces the pitch.
3. **Building** — Implement the shaped work within the appetite. The team has full autonomy on details.

### Appetite vs. Estimate

An **appetite** is a deliberate choice about how much time something is worth:
- "This problem is worth **2 weeks** of a team's time" (Small Batch)
- "This problem is worth **6 weeks** of a team's time" (Big Batch)

An **estimate** is a guess about how long something will take. Estimates expand to fill the available time and encourage gold-plating. Appetite constrains scope — if the solution doesn't fit the appetite, narrow the scope.

**"Good is relative."** There is no objectively "best" solution — goodness is always relative to the appetite. A six-week appetite produces a fundamentally different *kind* of solution than a two-week appetite for the same problem. Think of it like choosing between a hot dog and a ten-course dinner: the appetite doesn't just bound the work, it shapes the entire concept. Let the appetite actively reshape the solution, not merely trim its edges.

### The Circuit Breaker

Work that does not ship within its cycle is **cancelled by default**, not extended. There is no automatic continuation. This is the circuit breaker principle. It forces shaping to be honest about scope — if a pitch can't realistically ship within the appetite, it needs more shaping, not more time.

Exceptions are rare: extension only happens when (a) all outstanding work is true must-haves that survived repeated scope hammering, and (b) all remaining work is **downhill** — no unsolved problems, no open questions. Uphill work at the end signals a shaping or concept problem.

### Progressive Investment

Each phase narrows the focus and increases commitment:

1. Start with many possible **candidates** and choose one
2. **Frame** it to understand whether the problem is worth solving
3. Only after confirming the frame, invest the more expensive time in **shaping**
4. Only after confirming the shape, commit a full team to **building**

At each checkpoint, the work can stop. Framing might reveal the problem is not worth pursuing. Shaping might reveal the solution is too complex for the available appetite. This progressive narrowing prevents wasting expensive engineering time on poorly understood problems.

**The frame is the acceptance test for the shape.** If the shaped solution satisfies the frame, it is ready. If something is nice-to-have but not required to satisfy the frame, it is out of scope.

### Tracking Progress: Kanban Model

Track each piece of work through phases using a simple board:

```
Candidate → Framed → Shaping → Shape Go → Build → Shipped
```

Only advance work to the next column after the checkpoint passes. Most candidates never reach "Shaping" — they are narrowed down during framing.

### The Right Level of Abstraction

Shaping operates between abstract (too vague) and concrete (too detailed):

**Too abstract:** "Make the medication workflow better"
**Right level:** "Add a 'Dispense for period' function that reuses the dispensing flow but skips double-check, allows date range selection, and saves with optional comment"
**Too concrete:** "Put a blue button at coordinates (200, 300) that opens a modal with a date picker using react-datepicker..."

The goal: enough specificity that the team knows the boundaries, enough ambiguity that they choose the best implementation.

## Phase 1: Set Boundaries (Extended)

### Responding to Raw Ideas

The default response to incoming ideas is: **"Interesting. Maybe some day."** This is a soft no that preserves optionality. Do not say yes too quickly (creating premature commitments) and do not show too much enthusiasm (setting expectations). Ideas should not go into a backlog — they should float freely and resurface naturally if truly important.

### Identifying the Raw Idea

Raw ideas come from many sources:
- Customer requests ("We want to be able to...")
- Support tickets and repeated issues
- Internal staff observations
- Strategic goals
- Bug reports that reveal deeper problems

**Critical:** Raw ideas almost always contain a proposed solution mixed with the actual problem. Separate them.

**Example:**
- Raw request: "Add a comment field to medication dispensing"
- Surface solution: Add a text field
- Underlying problem: When medication is dispensed, there's no record of *why* or *for what purpose*, making it impossible to audit

### Narrowing the Problem

Ask these questions to narrow:
1. What is the actual workflow today? Walk through it step by step.
2. Where does it break down? What causes frustration or errors?
3. **When did you first want this? What were you doing at that moment?** Probe for the triggering moment and the broken workflow — not the desired feature.
4. What would "good enough" look like? Not perfect — just good enough.
5. Who is affected? One user type or many?
6. How often does this happen? Daily pain vs. occasional inconvenience.

### Watch for Grab-Bags

**Grab-bag projects** — vague scopes like "redesign the Files section" or anything labeled "2.0" — fail because there is no clear definition of "done." The remedy is to decompose them into problem-driven sub-projects with individual appetites. If a project cannot be expressed as a specific problem with a specific desired outcome, it is not ready for shaping.

### Finding the Nugget of Value

The goal is to find the smallest meaningful thing that solves the real problem — not to do everything. Each refinement should make the project more focused and more valuable.

**Example progression:** "Improve the dashboard" → "Surface metrics that matter to small gym owners" → "Show missed payments" → "Payment recovery workflow"

Each step narrowed the scope and increased the value. The SME confirmed that solving just the payment recovery was "a huge win" — he only mentioned class utilization because he was asked for more scope.

### Bringing the Right People Together

Shaping requires specific expertise at specific moments:
- **Subject matter expert (SME)** — Understands the real problem and domain
- **Senior engineer** — Understands what the codebase can and cannot do
- **Shaper** — Drives the process and maintains the right abstraction level

When open questions arise that the shaper cannot answer alone, bring in the right person. When possible, combine all three in one session (2 hours max) to avoid looping back and forth.

### Setting the Appetite

Choose the appetite based on strategic value, not implementation complexity:

| Appetite | When to use |
|----------|------------|
| Small Batch (1-2 weeks) | Clear problem, known solution pattern, limited scope |
| Big Batch (6 weeks) | Complex problem, multiple interacting parts, new territory |

If a problem doesn't fit either appetite, it's either too vague (needs more framing) or too big (needs to be split).

### Defining What's Out

Write explicit "no-gos." These prevent scope creep during building:
- "NOT including: search across all collections (only letters)"
- "NOT including: retrospective changes to historical records"
- "NOT including: integration with external calendars"

## Phase 2: Find the Elements (Extended)

### Parts/Mechanisms Table

Each part is a distinct component of the solution. Each mechanism describes how that part works.

Format:
```
| Part | Name | Mechanism |
|------|------|-----------|
| F1 | [Component name] | Summary: [How it works, what it adapts from] |
| F2 | [Component name] | Summary: [How it works] |
| ... | ... | ... |
```

**Tips:**
- Name parts after what they DO, not what they ARE
- Reference existing patterns: "adapts S-CUR3" means it follows an existing pattern
- Include the CMS/admin configuration parts — they're often forgotten
- Include cleanup: "Remove X from Y" is a valid part

### Breadboarding

A breadboard maps the flow without visual design. Three elements:

1. **Places** — Screens, pages, dialogs (boxes in the diagram)
2. **Affordances** — Things users can interact with: buttons, fields, links (labels inside places)
3. **Connections** — What leads where: clicks, submissions, navigations (arrows between elements)

**Text-based breadboard example:**
```
PLACE: Search Page
  - search input → triggers search
  - results grid → shows matching items
  - tile click → navigates to Detail Page

PLACE: Detail Page
  - back button → returns to Search Page (preserves search state)
  - content area → shows item details

SERVICES:
  - performSearch() → calls API, filters results
  - debounce (90ms, min 3 chars)
```

**Key principle from Ryan Singer:** "The trick is choosing the right level of abstraction. Rendering the full code would be a giant hairball. Like in architectural drawings, the 'affordances' are the simplifying concept: 'what are the things I can operate on from different perspectives.'"

### Fat Marker Sketches

When visual layout matters, sketch at a very rough level — as if drawing with a thick marker that prevents detail. Show arrangement and proportion, not design.

## Phase 3: Address Risks & Rabbit Holes (Extended)

### Thin-Tailed vs. Fat-Tailed Risk

Think of risk using probability distributions. Well-shaped work has a **thin tail**: it might take a few days longer, but it won't balloon. Poorly shaped work has a **fat tail**: it could consume multiples of the appetite without warning.

The goal of de-risking is to make the distribution thin-tailed. This happens when the solution consists of independent, well-understood parts that assemble in known ways. Fat tails come from open-ended exploration, unbounded integration problems, and parts whose complexity is unknown.

Before proceeding to write the pitch, ask: "Is this thin-tailed or fat-tailed?" If fat-tailed, more shaping is needed.

### R x F Fit Check Matrix

Cross-check every requirement against the shape:

```
| Req | Requirement | Status | Shape |
|-----|-------------|--------|-------|
| R0 | [Core goal of the project] | Core goal | Pass/Fail |
| R1 | [Must-have requirement] | Must-have | Pass/Fail |
| R2 | [Another requirement] | Must-have | Pass/Fail |
| R3 | [Feature explicitly excluded] | Out | X |
| R4 | [Undecided requirement] | Undecided | ? |
```

**Status categories:**
- **Core goal** — The primary thing the shape must solve
- **Must-have** — Required for the shape to be viable
- **Out** — Deliberately excluded (with explanation)
- **Undecided** — Needs resolution before building can start

**Actions after the fit check:**
- All must-haves pass → Shape is ready
- Must-have fails → Revise the shape to address it, or move requirement to "Out" with justification
- Undecided items → These are rabbit holes. Resolve or declare constraints.

### Common Rabbit Holes

Watch for these patterns:
- **Technical unknowns:** "Can we even do X with our current stack?"
- **Design unknowns:** "What should happen when edge case Y occurs?"
- **Integration unknowns:** "How does this interact with existing feature Z?"
- **Performance unknowns:** "Will this work with N thousand records?"
- **Migration unknowns:** "What happens to existing data?"

### Patching Rabbit Holes with Concrete Solutions

Do not just flag risks — provide specific, even compromised, solutions. The shaper makes pragmatic trade-offs that a team under deadline pressure cannot easily make.

**Example:** In a to-do grouping feature, the shapers decided that completed items would *not* be grouped — they would just be annotated with the group name. This was explicitly "a little messy" but it removed a huge risk (complex rendering logic for completed groups).

For each rabbit hole, declare a constraint that prevents it from consuming the appetite:

- "If calendar sync proves complex, skip it and use a simple date field"
- "Use existing search infrastructure; do not build a new search engine"
- "Handle the most common case only (80/20); edge cases go in a future cycle"
- "If we need more than 2 days on this sub-problem, cut it"
- "Completed items show group name as annotation, not actual grouping" (concrete patch)

### Presenting to Technical Experts

Before writing the pitch, bring a senior engineer to a whiteboard and **rebuild the concept from scratch** in front of them. Keep the clay wet — present it as "something I'm thinking about, not something coming down the pipe."

Critical framing: do not ask "is this possible?" (everything is possible given enough time). Ask **"is this possible within the appetite?"** This surfaces scope issues and technical risks that the shaper may have missed.

### Declaring Out of Bounds

Some rabbit holes are best handled by cutting scope rather than designing solutions. Declare explicitly: "We are NOT doing X." This is not a failure — it is a deliberate constraint that protects the appetite.

## Phase 4: Write the Pitch (Extended)

See `references/pitch-template.md` for the complete template.

### The Problem as Fitness Test

The problem statement is more than context — it is a **test of fitness** for the solution. The best problem definition consists of a single specific story that shows why the status quo doesn't work. People judge whether the solution makes this specific story better. Without a concrete problem, "there's no test of fitness to judge whether one solution is better than the other."

### Help Them See It

Raw breadboards have a "you had to be there" quality. For people who didn't watch the breadboard unfold, it can look like a soup of words and arrows. Use these techniques to make the solution legible:

- **Embedded sketches** — For "linchpin" parts of the design that everyone needs to see concretely, go one level deeper into fat-marker detail. Add a disclaimer that designers should feel free to find a different design.
- **Annotated fat marker sketches** — Redraw rough sketches with labels and call-outs. Use different colors to separate labels from the sketch. Keep the brush size thick to prevent unwanted detail.
- **Selective depth** — Not every part needs visual treatment. Only go deeper on parts that are inherently visual or too complicated for a schematic breadboard.

### Pitch Review Criteria

A pitch is ready when:
- A reader can understand the problem without prior context
- The problem is expressed as a single specific story (the fitness test)
- The appetite is explicit and justified
- The solution is described at breadboard level (not wireframes)
- Linchpin elements have embedded sketches to help readers "get" the concept
- Rabbit holes are identified with clear boundaries and concrete patches
- No-gos are listed explicitly
- A team could start building from this document within a day
- The shaped work is rough, solved, and bounded

### After the Pitch is Written

In the Shape Up methodology, pitches go to a **betting table** — a meeting where leadership decides what to commit to for the next cycle. The pitch competes with other pitches for the available appetite.

If a pitch is not bet on, it doesn't go into a backlog — it either gets reshaped with new framing for a future cycle, or it's dropped. There is no automatic carry-over.

### Betting Table Evaluation Questions

Five questions the betting table asks to evaluate a pitch. A well-shaped pitch should have clear answers to all five:

1. **Does the problem matter?** Weigh it against competing problems. Sometimes a too-complex solution signals the problem is not understood specifically enough.
2. **Is the appetite right?** If stakeholders resist the time commitment, probe whether the objection is about time or about something else (dependency, approach, design direction).
3. **Is the solution attractive?** Consider invisible costs — giving up screen real estate, adding complexity to the codebase. Avoid doing design work at the betting table.
4. **Is this the right time?** Balance new features vs. fixes. Consider team morale from doing the same kind of work repeatedly.
5. **Are the right people available?** Match projects to expertise. Consider what type of work each person has been doing recently.

### Scope Hammering and Must-Haves

During building, teams categorize discovered work as **must-haves** or **nice-to-haves** (marked with ~). Scope hammering is the practice of forcefully questioning every piece of work: Is this truly required to ship? Could we ship without it? Is this a new problem or one customers already live with?

Good shaping makes clear what is essential versus what is nice-to-have, enabling this cutting mechanism. When shaping, think: "If the team ran out of time, what could be dropped without losing the core value?"

### The Hill Chart

Progress on shaped work is tracked using the **hill chart**, not task counts. Each scope has two phases:
- **Uphill** — figuring out the approach, full of unknowns
- **Downhill** — execution, where remaining steps are visible and estimable

Shaping should aim to push as much of the concept downhill as possible before handing it off. If major scopes are still uphill after shaping, the shape is not ready.

## Building Phase Principles

Once shaped work is handed to the team:

### Build First, Polish Last

Start from the breadboard, wire up backend and frontend to get an "ugly but working prototype" that inherits existing styling. Only after all functionality works, apply visual design ("the paint") and polish. Like building a house: figure out where the sink and pipes go first; decide on paint color last.

### No Tickets, No User Stories

The team has a clear picture of the whole thing being built, broken into named vertical scopes. No individual tickets or user stories — the pitch and breadboard provide the complete context.

### Autonomy Through Clarity

Because the team has clarity from shaping and kickoff, they can work asynchronously for many days without regular status meetings. Progress is tracked through scopes (uphill/downhill), not through task burndown.

## Working with AI in Shaping

Ryan Singer's recent workflow demonstrates using AI as a shaping partner:

1. **Start with the existing system** — Before shaping a change, understand what the current system does and how it works. Map the existing architecture.
2. **Enumerate parts and mechanisms** — Let the parts table emerge from understanding the system, not from the feature request.
3. **Iterate the fit check** — Run the R x F matrix multiple times as the shape evolves. Each iteration reveals gaps.
4. **Break into slices** — After shaping, break the solution into vertical slices (V1, V2, ...) that each deliver working, demoable functionality.

### Slices Pattern

Slices are vertical cuts through the solution that each deliver complete functionality:

```
V1: [Core path works] — COMPLETE
    - Scope item 1
    - Scope item 2
    Demo: [What you can show]

V2: [Second capability works] — COMPLETE
    - Scope item 3
    - Scope item 4
    Demo: [What you can show]

V3: [Third capability] — IN PROGRESS
    ...
```

Each slice should be independently demoable and deliverable. The team works slice by slice, always having something that works.
