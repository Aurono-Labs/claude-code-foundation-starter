<!-- BOOTSTRAP INSTRUCTIONS FOR CLAUDE CODE — fill me in via interview

## Goal of this file
What's being built: the open phases and their items, done (✅) or pending (⬜).
Updated continuously through the 6-phase workflow, never in a separate
"documentation pass". Ideas live in `backlog.md`; closed phases move to
`project_history.md`, so this file only shows what's open.

## Interview prompts

1. "Is there work in progress already? Existing tickets, a Notion board,
   a GitHub project? Share it and I'll synthesize the initial phase
   structure."

2. If starting fresh on a green-field project:

   a) "What's Phase 0 — the foundation work that must happen before
      writing any product code? Things like: freeze terminology,
      define event taxonomy, lock contracts."

   b) "What's Phase 1 — the first product phase? It should match
      Phase 1 in docs/roadmap.md but break down into concrete
      sub-phases (1.1, 1.2, 1.3 …)."

3. For `backlog.md`: "Are there ideas already that didn't make it into a
   phase but should be remembered? List them with a one-line description each."

4. For the Parked section of `backlog.md`: "Are there ideas you considered
   and explicitly chose NOT to pursue (with a reason)? List them so future-you
   doesn't reconsider without seeing the prior reasoning."

## What the final file should look like

Replace this BOOTSTRAP block. Suggested structure:

```
# Project Plan — Master

This document is the **single source of truth** for the project.

Checked items (✅) are completed and frozen.
Unchecked items (⬜) are pending.

## What is this project?
<one-paragraph summary derived from vision_and_mission.md>

## PHASE 0 — <Foundation work> ✅
### 0.1 <step> ✅
- ✅ <action taken>
- ✅ <action taken>

(repeat per phase)
```

## Rules

- Don't rewrite completed items; mark them ✅. When the last open item of a
  phase closes, move the whole phase to `project_history.md`. An open item
  never sits in the history file, and a closed phase doesn't clutter the plan.
- The 6-phase workflow updates this file in Phase 4 and Phase 6 (completion
  marks). Backlog and parked items go to `backlog.md` in Phase 2.

## Example — how Aurono Labs answered this

> ## PHASE 0 — Freeze Reality (Before Writing Any Code) ✅
>
> ### 0.1 Freeze Aurono PoC behavior ✅
> * ✅ Document actual behavior (not intended behavior)
> * ✅ Include: strategy evaluation order, rounding & quantization rules,
>       capital sufficiency logic, known edge cases & "weirdness"
> * ✅ Saved as: `docs/aurono_PoC_behavior.md`
>
> ### 0.2 Declare compatibility boundaries ✅
> * ✅ Explicitly state what Aurono Start will not reproduce from PoC
> * ✅ Saved as: `docs/v1_non_goals.md`
>
> ## PHASE 1 — Canonical Contracts (No Runtime Code Yet) ✅
>
> ### 1.1 Finalize Aurono Event Taxonomy ✅
> * ✅ Freeze event names · Freeze semantic meaning · Versioned as
>       `event_taxonomy_v1.0`
>
> ## Backlog
> - 2026-04-09 — Scenario explorer for Lab
> - 2026-04-12 — Strategy health dashboard
> - 2026-04-19 — Demo mode for first-run experience

(The real Aurono project_plan.md is ~3,600 lines — phases 0 through 18, plus
backlog and parked items. The point isn't the volume; the point is that
every commit can be traced to a numbered item that was planned, executed,
and closed.)

Source: Aurono Start (reference implementation by Aurono Labs · auronolabs.com) · `docs/project_plan.md`.

END BOOTSTRAP -->

# Project Plan — Master

> Run `Bootstrap the foundation` to fill in.

This document is the **single source of truth** for the project.

Checked items (✅) are completed and frozen.
Unchecked items (⬜) are pending.

<!-- Open phase sections go here. Ideas: backlog.md. Closed phases: project_history.md. -->
