# Diagnostic Summary Template

Use this template to produce the final output of a diagnostic session.

**Handoff file path:** `docs/shapeup-handoff/<YYYY-MM-DD>-diagnose-<slug>.md`

---

## Diagnosis: [Short descriptive title — the diagnosed problem, not the original request title]

**Input:** [What was evaluated — original request title or one-line summary]
**Reporter:** [Who raised it, if known]
**Diagnosed by:** [Name], with Claude
**Verdict:** Shape this | Shoe insert | Go back and ask | Decompose | Let it go
**Confidence:** First-pass diagnosis — [ready for shaping / needs domain expert validation / needs more information]

**What this verdict means:** [Plain-language explanation of the verdict — see below]

- **Shape this** — This is a real problem worth investing time in. Next: define the solution approach.
- **Shoe insert** — Small fix — doesn't need a big project. Here's what to do.
- **Go back and ask** — We need more information before deciding. Here are the specific questions.
- **Decompose** — This is actually several problems bundled together. Let's separate them.
- **Let it go** — Not worth the investment right now. Here's why.

[Delete the options that don't apply — keep only the one matching the verdict above.]

---

### The Real Problem

[1-3 sentences describing the diagnosed root cause. This is NOT a restatement of the original request — it's the problem underneath the request. Write it as a problem statement, not a solution.]

### Why Not the Original Framing

[Explain the gap between what was requested and what the diagnosis found. Which lens revealed the most important insight? What was the symptom vs the disease?]

### Key Assumptions Surfaced

- **[Assumption 1]** — [Confirmed / Challenged / Unknown] — [Brief explanation]
- **[Assumption 2]** — [Confirmed / Challenged / Unknown] — [Brief explanation]
- **[Assumption 3]** — [Confirmed / Challenged / Unknown] — [Brief explanation]

[List the assumptions that were examined during the conversation. Mark each as confirmed (evidence supports it), challenged (evidence contradicts it), or unknown (need more information). Even 1-2 assumptions is fine — not every diagnosis surfaces many.]

---

### Recommendation

[Specific, actionable next step based on the verdict. Tailor this section to the verdict:]

#### If verdict is "Shape this":

**Reframed problem statement:** [The problem as it should enter shaping — not the original request wording]

**Suggested appetite range:** [Small batch / Big batch, with brief reasoning]

**Shaping starting points:**
- [What to investigate in Phase 1]
- [Key question to answer]
- [Constraint or boundary already identified]

*Next step: Use `shapeup:shaping` with this reframed problem.*

#### If verdict is "Shoe insert":

**The fix:** [Describe the small change — config, process, minor code tweak]

**Why this doesn't need shaping:** [It's small enough to just do]

#### If verdict is "Go back and ask":

**What we don't know:** [The gap in understanding]

**Questions for the reporter:**
1. [Specific question — not generic, targeted at validating a hypothesis]
2. [Specific question]
3. [Specific question]

**What the answers would tell us:** [How the answers change the diagnosis]

#### If verdict is "Decompose":

**Problems identified:**
1. **[Problem A]** — [One sentence description]
2. **[Problem B]** — [One sentence description]
3. **[Problem C]** — [One sentence description]

**Recommended first diagnosis:** [Which sub-problem to diagnose first and why]

#### If verdict is "Let it go":

**Why:** [Clear explanation — not dismissive, but honest]

**What would change this:** [Under what circumstances would this become worth revisiting]

---

### Shape Up Concepts Used

[Summarize which diagnostic concepts were applied during this session. This reinforces learning by naming what was practiced.]

- **[Term]** — [One-line explanation of what it means and how it applied here]
- **[Term]** — [One-line explanation of what it means and how it applied here]

[Only include concepts that were actually used in this diagnosis. Typical entries: "symptom vs disease," "solution masquerading as problem," "appetite," "grab-bag," "scope hammering," etc.]
