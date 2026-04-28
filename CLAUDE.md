# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A **Claude Code plugin** (`.claude-plugin/plugin.json`) that distributes Shape Up methodology to non-technical Danish consultants. Every file is markdown that ships as plugin content — no application code, no build/lint/test commands. Validation is by reading the markdown and checking that frontmatter, references, cross-skill routing, and handoff hooks stay consistent.

Consultants consume the plugin from a Claude cowork project that mirrors a team codebase (kept in sync via GitHub Desktop). Skills can therefore ask for code, screenshots, and file paths to ground the conversation — they do not assume an air-gapped consultant.

## Repository layout

```
.claude-plugin/plugin.json        # Plugin manifest
skills/shapeup/SKILL.md           # Front-door router (default entry point)
skills/<mode>/SKILL.md            # explore | diagnose | shaping
skills/<mode>/references/*.md     # Long-form material the skill links to
docs/shapeup-handoff/             # Output directory for handoff artifacts (consultant-side)
```

`docs/shapeup-handoff/` is not committed to this repo — it lives in the consultant's cowork project. The path is referenced from each skill's handoff phase; if you change it, change it everywhere.

## How the skills compose

The plugin has four skills that compose as one front-door + three modes:

- **`shapeup`** — default front door. Triggers on any feature request, bug, customer complaint, idea, "I want to build/fix X" prompt. Reads the prompt, picks a mode silently (no menu, no "which one would you like"), and runs that mode's process. Defaults to `diagnose` when ambiguous.
- **`explore`** — vague idea, nothing concrete to attack. Coffee conversation. Hands off forward.
- **`diagnose`** — concrete request that might be the wrong problem. Five lenses (symptom vs disease, scope boundaries, solution-as-problem, process vs software, unsurfaced assumptions). Five verdicts (*Shape this / Shoe insert / Go back and ask / Decompose / Let it go*).
- **`shaping`** — problem is real, produces a pitch via Set Boundaries → Find the Elements → Address Risks → Write the Pitch.

Cross-references between skills are load-bearing. The `shapeup` router reads `skills/<mode>/SKILL.md` directly, and each mode references the others for transitions. Renaming or deleting a skill requires fixing every reference, every routing table, and every frontmatter `description` that lists trigger phrases.

## Mandatory handoff (every session)

Each mode ends with the same interactive prompt — not silent auto-write, not optional:

> **Want to package this up?**
> a) Produce handoff bundle — writes markdown to `docs/shapeup-handoff/<YYYY-MM-DD>-<mode>-<slug>.md`
> b) No handoff — end without a file

If the user picks (a), Claude confirms the slug, uses the Write tool, and announces the path. Filenames are kebab-case and prefixed with the date and mode. The handoff is the deliverable — consultants used to copy raw transcripts, which the artifacts replace.

When editing skills, preserve this prompt verbatim across all three modes — it is the only place the consultant has explicit control over output.

## Scope: framing tool, not implementation tool

This plugin produces a **brief** — problem definition, diagnostic verdict, or pitch — that goes to a developer. Developers do the technical assessment, push back on assumptions the plugin missed, and find better paths. The plugin does not propose code changes, file edits, or implementation steps.

Every skill includes a scope-pushback rule: if the consultant asks for code or "just build it", Claude declines softly and routes back to the current phase or the handoff prompt. Preserve this rule when editing — it is the line between "clean brief for a developer" and "well-formatted wrong thing shipped".

## Flavor

Each skill carries a small Danish easter-egg block — sparing, dry, deadpan lines like *"Morten er stolt af dig"* or *"Rough, solved, bounded — Morten nikker"* — used **at most once per session at a moment of genuine progress**. Tone is dry-Danish, never cheerful. The joke is the unexpected internal-reference, not the praise. Don't expand these into a system that fires every message.

## Audience constraints (these shape every editorial decision)

End users are **non-technical Danish consultants** who don't know Shape Up vocabulary and don't know which slash command they need.

- **Intent routing, not user routing.** The consultant types their problem; `shapeup` decides the mode. Never ask "do you want to explore, diagnose, or shape?" — they don't know.
- **Concise and interactive, not pedagogical.** Skills must use one-question-per-message and multiple-choice patterns. Long narrative explanations belong in `references/`, not `SKILL.md`. Don't reintroduce "Teaching Approach" sections — they were removed deliberately.
- **Ground in the user's product.** Consultants have code access via the cowork project. Ask for code, screenshots, file paths whenever it makes the conversation concrete. Don't fabricate product details.
- **Shaping pitches are unvalidated by default.** `shaping` mandates `Confidence: First-pass shape — needs technical review` until a senior engineer signs off. Don't loosen this.
- **Bilingual Danish/English.** Conversation matches the user (Danish in → Danish out). Shape Up vocabulary (appetite, pitch, breadboard, grab-bag, scope hammering, rabbit hole, R×F fit) **stays in English** — it is the cross-team shared vocabulary. Brief Danish anchors when introducing a term for the first time are encouraged; full translations are not.

## Skill authoring conventions

- **Frontmatter `description` is the trigger.** It must be packed with the natural-language phrases consultants actually type, in both Danish and English where useful. The `shapeup` router's description is intentionally broad — it is the catch-all front door.
- **Voice is instructional to Claude, not to the user.** SKILL.md tells Claude how to behave; the consultant never reads it.
- **Output templates and long examples live in `references/`.** SKILL.md links to them; it does not inline them.
- **Phase tables, verdict tables, routing tables are the contract.** The five verdicts in `diagnose`, the four phases in `shaping`, the routing table in `shapeup`, and the handoff prompt in every mode are referenced from each other and from this file. Changing names ripples everywhere.

## Plugin metadata

`.claude-plugin/plugin.json` — bump `version` whenever skill behaviour or routing changes. `keywords` drive plugin discovery; keep them aligned with the skills' actual coverage.
