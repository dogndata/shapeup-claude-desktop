# Pitch Template

Use this template to write the final shaped work document. Adapt sections as needed — not every pitch needs every section in full detail.

---

## [Pitch Title]

**Appetite:** [Small Batch: 1-2 weeks / Big Batch: 6 weeks]
**Shaped by:** [Name(s)], with Claude
**Date:** [YYYY-MM-DD]
**Status:** [Draft / Ready for betting / Bet / Building / Shipped]
**Confidence:** [First-pass shape — needs technical review / Technically validated / Ready for betting]

---

### 1. Problem

Describe the raw idea and the underlying problem it addresses. The best problem definition is **a single specific story** showing why the status quo doesn't work. This story becomes the fitness test for judging the solution.

**Trigger:** What event or observation prompted this work?

**The specific story:** Walk through one real scenario where the current workflow breaks down. Be concrete — name the user type, the task, and the moment of pain.

**The pain:** What is broken, slow, confusing, or missing? Who is affected and how often?

**Baseline:** What are customers doing today without this feature? (This is the comparison standard — "better than baseline," not "perfect.")

**Why now:** What makes this worth addressing in the next cycle? What strategic goal or pressure is driving it?

---

### 2. Appetite

State the time budget and justify it.

**Time budget:** [1 week / 2 weeks / 6 weeks]

**Justification:** Why is this amount of time appropriate for this problem? What kind of solution does this appetite afford? (Remember: the appetite changes the *kind* of solution, not just the scope.)

**Scope constraint:** What would a version of this look like if constrained to half the appetite? (This helps identify the core.)

---

### 3. Solution

#### Parts / Mechanisms

| Part | Name | Mechanism |
|------|------|-----------|
| F1 | [Part name] | [How it works] |
| F2 | [Part name] | [How it works] |
| F3 | [Part name] | [How it works] |
| ... | ... | ... |

#### Breadboard

Describe the flow using Places, Affordances, and Connections:

```
PLACE: [Screen/Page Name]
  - [Affordance] → [Connection/Action]
  - [Affordance] → [Connection/Action]

PLACE: [Screen/Page Name]
  - [Affordance] → [Connection/Action]
```

Or use a text-based flow description if a diagram is not needed.

**Help them see it:** For "linchpin" parts of the design, include embedded fat-marker sketches so readers can visualize the concept. Add a disclaimer that designers have latitude to find a different design. Keep sketches rough — thick brush, minimal detail, labeled clearly.

#### Key Design Decisions

List any important decisions made during shaping that the team should know about:
- "Use [existing pattern X] for [component Y]"
- "[Component Z] does NOT need [feature W] because..."
- "Data flows from [A] to [B] via [C]"

---

### 4. Rabbit Holes

List identified risks and how they are bounded. Provide **concrete patches** — specific, even compromised, solutions that remove risk. Do not just flag problems; resolve them.

| Risk | Patch / Boundary |
|------|------------------|
| [Technical unknown] | [Specific constrained solution] |
| [Design unknown] | [Decision made, even if imperfect] |
| [Integration risk] | [Approach chosen or declared out of bounds] |

**Technical validation:** Has a senior engineer reviewed this shape and confirmed it is feasible within the appetite?

---

### 5. No-Gos

Explicit list of what is NOT included in this pitch, even if related or requested:

- NOT: [Feature/scope explicitly excluded]
- NOT: [Another exclusion]
- NOT: [Another exclusion]

**Reason:** [Brief explanation of why these are excluded — typically appetite constraint, separate problem, or insufficient understanding]

---

### 6. R x F Fit Check (Optional)

Include when the pitch has enumerable requirements to verify against the shape.

| Req | Requirement | Status | Fit |
|-----|-------------|--------|-----|
| R0 | [Core goal] | Core goal | [Pass/Fail] |
| R1 | [Requirement] | Must-have | [Pass/Fail] |
| R2 | [Requirement] | Must-have | [Pass/Fail] |
| R3 | [Requirement] | Out | X |

**What's Unsolved:** [Description of any undecided items and what needs to happen before building]

---

### 7. Suggested Slices (Optional)

If the solution naturally breaks into vertical slices, list them:

| Slice | Name | Scope |
|-------|------|-------|
| V1 | [First deliverable] | [Key items] |
| V2 | [Second deliverable] | [Key items] |
| V3 | [Third deliverable] | [Key items] |

Each slice should be independently demoable.

---

### Shape Up Concepts Used in This Pitch

A summary of the methodology concepts applied during shaping, for reference and learning:

- **[Concept]** — [How it was applied in this pitch]
- **[Concept]** — [How it was applied in this pitch]
- **[Concept]** — [How it was applied in this pitch]

---

## Quality Checklist

Before submitting this pitch, verify:
- [ ] **Rough** — Solution is at breadboard level, not wireframes or detailed specs
- [ ] **Solved** — Main elements are defined, key questions answered
- [ ] **Bounded** — Appetite set, no-gos explicit, rabbit holes patched
- [ ] **Problem as fitness test** — A specific story makes it easy to judge the solution
- [ ] **Thin tail** — No unbounded risks that could balloon the project
- [ ] **Technical validation** — A senior engineer confirmed feasibility within the appetite

## Notes

- This pitch follows the Shape Up methodology (basecamp.com/shapeup)
- The appetite is a constraint, not an estimate — it changes the *kind* of solution
- The building team has autonomy over implementation details within the shaped boundaries
- If this pitch is not bet on, it does not go into a backlog — it is dropped or reshaped fresh
