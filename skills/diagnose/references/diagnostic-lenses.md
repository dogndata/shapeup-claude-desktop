# The Five Diagnostic Lenses

Each lens is a different angle of critical examination. Apply all five to every request. Some will yield strong hypotheses, others will yield "nothing notable here" — that's fine. The value is in the systematic coverage.

## Lens 1: Symptom vs Disease

**The question:** Is the reported problem the root cause, or a downstream effect of something else?

**How to apply:**
- Read the request and identify what the reporter says is broken
- Ask: "If we fixed exactly what they're asking for, would the underlying situation actually improve?"
- Ask: "What causes this situation to exist in the first place?"
- Look for chains: A causes B causes C — the reporter sees C, but A is the root

**Example:**
- **Reported:** "We need a deviation overview for the department"
- **Symptom:** Checking 26 residents for medication deviations is tedious (steps 1-7 repeated 26 times)
- **Possible disease:** There's no batch/aggregate view for department-level medication status. The deviation check is just one manifestation — the same structural problem likely affects other department-level tasks.

**Red flags that suggest symptom, not disease:**
- The request describes a workaround ("we currently do X to get around Y")
- Multiple similar requests exist for the same area
- The reporter describes many steps but the pain is concentrated in one transition
- The request has been asked for before in slightly different forms

## Lens 2: Scope Boundaries

**The question:** What part of the described problem is actually within our domain to solve? What's been inflated?

**How to apply:**
- Map out every step/actor in the described workflow
- Mark which steps involve our software vs external processes, other people, regulations, or other systems
- Identify where the reporter's scope ends and someone else's begins
- Count: how many steps are actually ours?

**Example:**
- **Reported:** 19-step medication deviation workflow is painful
- **Analysis:** Steps 1-7 are the department lead finding deviations. Steps 8-18 are the responsible nurse registering and commenting on each deviation. Step 19 is repeating the whole process days later.
- **Our scope:** Steps 1-7 (finding deviations) are where our software can help. Steps 8-18 are a different person's workflow with different constraints. The 19-step framing makes it look 3x worse than the part we can actually address.

**Red flags that suggest inflated scope:**
- The workflow description involves multiple people/roles
- Steps switch between "I do" and "they do" or "someone has to"
- The step count is high but many steps are outside the software
- The reporter includes organizational/process steps as if they're software steps

## Lens 3: Solution Masquerading as Problem

**The question:** Is the reporter describing what's broken, or describing what they want built?

**How to apply:**
- Separate statements of pain ("it's hard to...", "we can't...", "it takes too long to...") from statements of solution ("we need a button that...", "add a field for...", "it should work like...")
- If the request is >80% solution language, the actual problem may be unstated
- Ask: "What would they do differently if this solution existed?" — the answer reveals the real problem

**Example:**
- **Reported:** "We need comments on dispensing"
- **Solution language:** "Add a comment field", "make it bold and clickable", "show in overview"
- **Unstated problem:** Staff are registering fake deviations just to attach notes to dispensing events. The real problem is that there's no way to annotate medication events outside the deviation system. The solution jumped straight to "comment field" without examining whether the deviation workaround reveals a deeper annotation gap.

**Red flags that suggest solution-as-problem:**
- The request reads like a feature spec, not a pain description
- UI details are specified (colors, placement, click behavior)
- The word "should" appears more than "can't" or "hard to"
- The reporter references an existing feature to copy ("like X but for Y")

## Lens 4: Process vs Software

**The question:** Does this need a code change, or is the real solution a workflow/process change?

**How to apply:**
- Ask: "If we changed how people work (not the software), could this problem go away?"
- Ask: "Is the software forcing a bad process, or is the process bad regardless of software?"
- Consider: training, checklists, role changes, communication patterns, scheduling

**Example:**
- **Reported:** "Task repetitions on tasks — like we have on citizen tasks"
- **Process question:** Why are tasks repeating? Is it because the same task genuinely recurs on a schedule? Or is it because staff forget to do them and need reminders? If it's reminders, maybe a morning checklist or a shift handover process solves it better than cluttering the calendar.
- **Software question:** If tasks genuinely recur (e.g., weekly medication review), then software repetition makes sense. But the comment "risk of calendar becoming overfull and colorful" suggests the calendar wasn't designed for this density — adding repetitions might create a new problem.

**Red flags that suggest process problem:**
- The request is about communication or coordination between people
- The described pain involves "forgetting" or "not knowing"
- The solution would add complexity to an already complex interface
- Other organizations handle this without software support

## Lens 5: Unsurfaced Assumptions

**The question:** What do we believe about how people actually work — and is it true?

This is the most important and most difficult lens. The other four challenge the *request*. This one challenges *your own mental model*.

**How to apply:**
- List what you assume about the user's workflow, environment, frequency, and context
- For each assumption, ask: "How do I know this? Have I observed it, or am I projecting?"
- Ask the user to walk through what actually happens — not the ideal process, but reality
- Listen for surprises: "Oh, they do it daily? I assumed it was weekly."

**Example:**
- **Assumption:** "Nurses check medication deviations daily as part of their routine"
- **Challenge:** Do they? Or do they only check when prompted by a supervisor? If it's supervisor-prompted, the real problem might be "supervisor has no easy way to trigger and track deviation reviews" — a completely different problem than "nurse needs a faster deviation workflow."

**Techniques for surfacing assumptions:**
- "Walk me through what actually happens on a typical day when this comes up"
- "You said [X] — is that always the case, or are there exceptions?"
- "How do you know that's how they use it?"
- "What would surprise you if you watched someone do this over their shoulder?"
- "Are we assuming this works the same way at every location/department?"

**Red flags that suggest hidden assumptions:**
- You immediately know the solution ("obviously we should...")
- The request seems straightforward and uncontroversial
- No one has questioned the premise
- The request comes from someone who isn't the end user
- You've never actually watched someone do this workflow
