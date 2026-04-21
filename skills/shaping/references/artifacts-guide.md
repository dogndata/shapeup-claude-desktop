# Shaping Artifacts Guide

This reference shows how to create the concrete artifacts produced during shaping: Parts/Mechanisms tables, Breadboards, R x F Fit Check matrices, and Slices.

## Working with Non-Technical Collaborators

The artifacts below are powerful thinking tools — but they can feel intimidating to someone encountering them for the first time. When co-creating these with non-technical colleagues:

### Breadboarding Through Dialogue

Don't present an empty breadboard template. Build it together through questions:

1. "Where does this start? What screen or page is the person on?"
   → That gives you the first PLACE

2. "What do they see there? What can they interact with?"
   → Those are AFFORDANCES

3. "When they [do the thing], what happens? Where do they end up?"
   → That's a CONNECTION to the next PLACE

4. After each answer, write the breadboard notation and show it:
   "OK so our breadboard looks like this now:
   PLACE: Medication Overview
     - deviation flag → shows details
   Does that match what you're describing?"

5. Iterate: "What's missing? What else can they do here?"

### Parts/Mechanisms Through "Bill of Materials"

Frame it as: "Let's list the moving pieces of this solution. For each piece, what does it do and roughly how?"

Start with: "What's the most important piece?" → That's F1.
Then: "What else do we need for this to work?" → Build the table together.

### R x F Fit Check as "Did We Miss Anything?"

Frame it as: "Let's check our solution against what we need. For each requirement, does our solution handle it?"

Walk through requirements one by one. For each: "Does our shape cover this? Yes, no, or we're not sure?"

## Parts / Mechanisms Table

The parts table is the "bill of materials" for the shaped solution. Each row describes one distinct component and how it works.

### Format

```markdown
| Part | Name | Mechanism |
|------|------|-----------|
| F1 | Create new widget | Component, definition file, register in map, receive parentId via data, add to module |
| F2 | URL state & initialization | queryParams provides (q, page), initializeState() reads URL, triggers initial fetch |
| F3 | Search input | Input binds to BehaviorSubject, debounced subscription, min 3 chars triggers search |
| F4 | Data fetching | performSearch() sets loading, calls rawSearch() with filter, writes results to state |
| F5 | Pagination | Scroll-to-bottom via scroll service, increment page, concat hits, update URL |
| F6 | Rendering | Loading spinner, "no results", +ngFor rows (reuse existing tile component), tile click navigates |
| F7 | Remove from widget-grid | Remove branch from routing, remove type dropdowns, widget-grid unchanged for other types |
| F8 | CMS configuration | Admin places widget via CMS, backend delivers with parentId, no code changes for routing |
```

### Guidelines

- **Name after what the part DOES** — "Data fetching" not "The fetch service"
- **Reference existing patterns** — "(adapts S-CUR3)" signals reuse of known code
- **Include non-obvious parts** — Configuration, cleanup, migration steps
- **Keep mechanisms at summary level** — Enough to understand the approach, not enough to implement
- **Number sequentially** — F1, F2, ... for easy reference

### When to Use

Create a parts table when:
- The solution has 3+ distinct components
- Multiple people need to understand the scope
- Technical approach decisions need to be captured

## Breadboard

A breadboard maps the user flow and system interaction without visual design. It uses three elements:

### The Three Elements

1. **Places** — Named locations in the interface (screens, pages, dialogs, panels)
2. **Affordances** — Things within a place that users can interact with (buttons, inputs, links, toggles)
3. **Connections** — What happens when an affordance is used (navigation, state change, API call)

### Text Format

```
PLACE: Search Page
  - search input (text field)
    → on type: debounce 90ms, min 3 chars
    → triggers performSearch()
  - results grid
    → shows matching items as tiles
    → scroll to bottom: load next page
  - tile click → navigates to Detail Page

PLACE: Detail Page
  - back button → returns to Search Page (preserves search/pagination state)
  - content area → shows item details
  - edit button → opens Edit Dialog

SERVICES:
  - performSearch(query, page) → calls API, returns results
  - initializeState() → reads ?q= and ?page= from URL on load
```

### Diagram Format

When a visual diagram helps, use this structure:

```
┌─────────────────────┐
│   PLACE: Search     │
│                     │
│  [search input]     │──→ performSearch()
│  [results grid]     │──→ tile click ──→ Detail Page
│  [pagination]       │──→ load more
└─────────────────────┘
         ↑
         │ back (preserves state)
         │
┌─────────────────────┐
│  PLACE: Detail      │
│                     │
│  [back button]      │
│  [content]          │
│  [edit button]      │──→ Edit Dialog
└─────────────────────┘
```

### Key Principle: Right Level of Abstraction

From Ryan Singer: "The trick is choosing the right level of abstraction. Rendering the full code would be a giant hairball. The 'affordances' are the simplifying concept: 'what are the things I can operate on from different perspectives.'"

Think of breadboarding as generating the **affordances** of the system — the interaction points that matter, stripped of implementation detail.

### Breadboarding as a Debate Engine

Breadboarding is not just documentation — it is a **thinking and debate tool**. Drawing the flow surfaces hidden questions that would otherwise emerge during building.

**Example:** When breadboarding an Autopay feature, drawing the flow surfaced the question "did we actually pay the original invoice?" This led to an entirely different starting point for the flow. The notation *provokes* decisions by making implicit assumptions explicit.

When breadboarding, expect surprises. Each element drawn raises questions: "What happens if...?" "Where does this data come from?" "What if this is empty?" These questions are the whole point — discovering them now is far cheaper than discovering them during building.

### When to Use

Create a breadboard when:
- The solution involves navigation between multiple places
- User flow is non-trivial (more than one step)
- Technical and non-technical stakeholders need to align on behavior

## R x F Fit Check Matrix

The R x F Fit Check cross-references **Requirements** against the **current shape (F)** to verify coverage and identify gaps.

### Format

```markdown
| Req | Requirement | Status | F |
|-----|-------------|--------|---|
| R0 | Make items searchable from the index page | Core goal | Pass |
| R1 | Make search generic for all collections | Out | X |
| R2 | Navigate back to pagination state from detail | Must-have | Pass |
| R3 | Navigate back to search state from detail | Must-have | Pass |
| R4 | Search/pagination state survives page refresh | Must-have | Pass |
| R5 | Browser back button restores previous state | Must-have | Pass |
| R6 | Maps 1:1 with data source | Must-have | Pass |
| R7 | Non-target displays continue unchanged | Must-have | Pass |
| R8 | Language switching not required | Must-have | Pass |
| R9 | Search debounce (not fire on every keystroke) | Must-have | Pass |
| R10 | Require minimum 3 characters | Must-have | Pass |
| R11 | Loading and empty states provide feedback | Must-have | Pass |
| R12 | Handles both abbreviated and full page display | Undecided | ? |
```

### Status Categories

| Status | Meaning | Action |
|--------|---------|--------|
| **Core goal** | The primary thing this shape exists to solve | Must pass |
| **Must-have** | Required for the shape to be viable | Must pass |
| **Out** | Deliberately excluded from this shape | Mark X, document why |
| **Undecided** | Not yet determined if needed | Resolve before building |

### After the Fit Check

Document what remains unsolved:

```markdown
**What's Unsolved:**

R12 remains undecided. The question: does the widget need to handle
two display modes?
- Abbreviated — mixed with other widgets on a page
- Full page — dedicated browsing experience

Shape F currently assumes full-page display only. If R12 becomes a
must-have, the shape needs a mechanism for abbreviated mode.
```

### Iterating the Fit Check

The fit check is not one-and-done. Run it:
1. **After initial shape** — Identify gaps early
2. **After revising the shape** — Verify fixes actually work
3. **Before writing the pitch** — Final verification

### When to Use

Create an R x F Fit Check when:
- There are 5+ distinct requirements
- Multiple stakeholders have different expectations
- The shape went through iterations and coverage is unclear
- Customer requests contain many individual items to verify

## Slices

Slices break the shaped solution into vertical cuts that each deliver working functionality.

### Format

```markdown
| Slice | Name | Status | Scope |
|-------|------|--------|-------|
| V1 | Widget with Real Data | COMPLETE | Create widget, register in CMS, rawSearch() with parentId, loading/empty/results UI |
| V2 | Search Works | COMPLETE | Search input + activeQuery, debounce 90ms min 3 chars, query passed to rawSearch() |
| V3 | Infinite Scroll | COMPLETE | Intercom scroll subscription, appendNextPage(), re-arm scroll detection |
| V4 | URL State | COMPLETE | ?q= in URL, initializeState() on load, Router.navigate() on change, back button restores |
| V5 | Compact Mode | COMPLETE | data compact config, conditional scroll subscribe, "See all X results" link |
| V6 | Cutover | COMPLETE | Delete protection, index job, page size fix, deploy code, CMS cutover |
```

### Slice Design Principles

- **Each slice is independently demoable** — "Demo: Type 'dallas', results filter live"
- **Order by dependency and risk** — Put the riskiest slice first (get unknowns resolved early)
- **Include a cutover/deployment slice** — Don't forget the work of shipping
- **V1 should prove the concept** — If V1 works, the rest is execution

### When to Create Slices

Create slices:
- After the pitch is approved and before building begins
- When the solution has 3+ parts that can be delivered incrementally
- To help the building team self-organize their work

## Common Patterns

### Adapting Existing Features

When a shape reuses existing code patterns, call it out explicitly:
- "F2: URL state & initialization **(adapts S-CUR1)**"
- "Reuse dispensing flow but skip double-check step"
- "Follow the same pattern as helbredsnotater attachment"

This reduces risk (known approach) and helps estimation.

### Cleanup Parts

Shapes often include removing or simplifying existing code:
- "F7: Remove letters from widget-grid — Remove branch from routing, remove year/type dropdowns"

Include these as explicit parts. They have scope and can contain surprises.

### Configuration Parts

Don't forget configuration and admin setup:
- "F8: CMS configuration — Admin places widget via CMS, backend delivers with parentId"

These are often the difference between "it works in dev" and "it's actually shipped."
