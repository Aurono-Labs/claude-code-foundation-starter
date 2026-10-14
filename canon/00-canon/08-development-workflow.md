# Development Workflow

> Pre-filled: this is the method, not an interview answer. During `Bootstrap the canon`, walk the operator through it and ask only which steps to drop or add. Record any change with its date.

Every product follows this six-phase cycle. Each product's `CLAUDE.md` reproduces the phases with its own file names and commands, and says at the top: *"The workflow below follows `<org>-canon/00-canon/08-development-workflow.md`."* Keep the phases, triggers and checkpoints; localize the rest. Don't copy this file's prose wholesale.

## Phase 1: Idea intake

**Trigger:** "New idea: <description>"

Respond with an assessment:
- **Canon alignment**: does it fit `01-values-and-vision.md`? Cite the belief; don't restate it.
- **User value**: what does this add, and for whom?
- **Effort**: S / M / L.
- **Complexity**: Low / Medium / High (architectural impact, edge cases).
- **Recommendation**: build now, backlog or park, with a short reason.

No file changes in this phase. The operator decides next.

## Phase 2: Backlog or park

**Trigger:** "Add to backlog" or "Park this"

Append to the product's backlog file with the date and a short description, or to its Parked section with the reason. Show the appended lines. Nothing else changes.

Keep the backlog in its own file, separate from the project plan. The plan holds what's being built; the backlog holds what might be. A plan that also carries hundreds of ideas stops being readable.

## Phase 3: Planning

**Trigger:** "Let's build <item>"

Write the full plan before any code:
1. **Goal**: one sentence.
2. **Affected modules**: which files, and why.
3. **Implementation steps**: numbered, small enough to execute one at a time.
4. **Tests**: exact test names, grouped by file.
5. **Functional tests**: the exact entries to add to the functional test log.
6. **Canon check**: user-facing copy against `04-tone-of-voice.md` and `07-writing-style-guide.md`; visual work against `02-design-system.md` and `03-ux-principles.md`; new words against `05-terminology.md` and the product's own glossary.
7. **Architectural decisions**: deviations from or additions to the architecture.

Wait for explicit approval before writing code.

**Large work goes in phases.** Merge each phase to the main branch before starting the next one. A long-lived branch carrying three phases is hard to review and hard to roll back.

## Phase 4: Execution

**Trigger:** "Plan accepted"

Write the code and the tests, run the suite, append the functional test entries (status: open), update the product's docs. New user-facing copy is checked against canon before it counts as done, not after.

- **Don't deviate from the approved plan.** If a problem needs a deviation, or the plan turns out unsafe halfway, stop and present it.
- **Discuss before building.** A question, an idea or a reported issue is not a request to write code. Discuss, propose options, wait for approval, then build.
- **Verify with real data.** When the product has a dev database, a running instance or production copies, pull the evidence yourself rather than asking the operator to check. When a tool or another model makes a claim about the data, check it against the data before recording it.
- Every small tweak during a build is still Phase 4. Do not commit or push; wait for the operator to test.

## Phase 5: Functional testing

The operator tests on their own machine and closes the open entries.

- Claude may run and close entries that need no human eyes (backend behavior provable by tests and API calls). Entries that need a browser, a device or a judgment stay open for the operator.
- The functional test log is historical. When configuration or behavior changes later, add new entries; don't rewrite old ones. They record what was tested at the time.

## Phase 6: Closing

**Trigger:** "Functional tests closed", or the operator confirms.

1. Commit to a feature branch, push, open a pull request. Docs and functional test updates ride in the same pull request as the code; no docs-only branches.
2. Update the product's docs: plan (mark done with the date), architecture, test inventory, user journeys if one changed. When the last open item of a plan phase closes, move the phase to the history file, so the plan only shows what's open.
3. **Sibling check.** If this product forked, or was forked from, another product's code: does this fix or change apply there too? Bug fixes especially; a shared core means a shared bug. Add it to the sibling's backlog; don't assume its own workflow will find it.
4. **Support-docs check.** If the change is user-facing and support docs live elsewhere (a website, a help center), do they now describe old behavior?
5. **Canon drift check.** Did this work introduce a deliberate deviation from canon? Propose a line for `01-products/<product>.md`. Accidental drift? Propose the fix.
6. If the work taught a rule worth keeping, propose it for the product's `CLAUDE.md`, or for canon if it holds for every product.

## Session hygiene

Suggest a fresh session when a major piece of work is committed, after three to four hours of work, after several workflow steps were skipped or corrected, or after a heavy documentation sweep. The rules in `CLAUDE.md` and memory load cleanly at session start and fade under task detail in a long one.

Before closing: commit or note pending work, save new feedback to memory, summarize the state for the next session.

## Why this lives in canon

The shape (triggers, checkpoints, what gets checked when) is what's shared and worth protecting. File names, test frameworks and deployment mechanics differ per product and stay local.
