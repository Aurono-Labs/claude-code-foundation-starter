# Project Conventions

<!-- BOOTSTRAP INSTRUCTIONS FOR CLAUDE CODE — read me at session start

This is the **keystone file** for the project's documentation foundation. It is
intentionally generic. The first time the operator runs this project through
Claude Code, walk them through the BOOTSTRAP PROTOCOL below to fill in their
specifics. Until that is done, treat this file as scaffolding, not a contract.

After bootstrap is complete, remove this comment block and replace the placeholders
(`<...>`) with the operator's confirmed content.

## Origin

This pack codifies the working method developed at **Aurono Labs**
(auronolabs.com) — an organization building local-first, execution-only
infrastructure for personal capital — while shipping their first product,
**Aurono Start**: a local-first crypto trading application that runs on
the user's own hardware. The Aurono Start repository is the reference
implementation of this method.

Every foundation file in `docs/` includes an "Example — how Aurono Labs
answered this" block drawn from the real Aurono Start documentation, so
you can see the shape and quality bar of a good answer before the
operator's interview begins.

END BOOTSTRAP -->

> **Status:** scaffold — run `Bootstrap the foundation` to fill in.

---

## Running & Installing

| Task | Command | Notes |
|---|---|---|
| Dev (backend + frontend) | `<dev command>` | |
| Install (production) | `<install command>` | |
| Build release artifact | `<build command>` | |

## Tests

| Suite | Command | When |
|---|---|---|
| Fast suite | `<fast test command>` | Default |
| Full suite | `<full test command>` | Touching core engine |

## Git

- **Main branch**: `<main branch name>`
- **Feature branches**: short-lived, named `feature/<short-name>`, branched off main, merged via PR, deleted after merge.
- **Pre-commit hook**: optional — blocks commits touching user-facing code unless `docs/functional_tests.md` is also updated.

---

# Bootstrap Protocol

**Trigger:** the operator types `Bootstrap the foundation` or this is the first session in a project where the docs/ folder still contains `<!-- BOOTSTRAP INSTRUCTIONS -->` blocks.

Walk through the foundation files in this exact order. For each file:

1. Read the file's BOOTSTRAP block to understand what shape the content should take.
2. Ask the operator if they have existing material to draw from (PDF, slides, web page, internal wiki, notion doc, previous repo). Offer to read it if they paste a path or URL.
3. If no material exists, conduct the interview using the prompts in that file's BOOTSTRAP block.
4. Synthesize the answers into the file's structure. **Never invent content** — if the operator can't answer a section, mark it `TODO` and move on.
5. Show the operator the proposed file content before saving. Wait for confirmation.
6. On confirmation, write the file (removing the BOOTSTRAP block in the process).
7. Move to the next file.

**Order:**

1. `docs/vision_and_mission.md`
2. `docs/roadmap.md`
3. `docs/domain_terminology.md`
4. `docs/non_goals.md`
5. `docs/architecture.md`
6. `docs/project_plan.md`
7. `docs/design/design_system.md`
8. `docs/design/user_journeys.md`
9. `docs/testing/test_suite.md`
10. `docs/functional_tests.md`

11. **Finally:** revisit this file (`CLAUDE.md`). Use the answers from the interview to fill in the placeholders above (commands, main branch name, etc.) and update the section below ("Vision & Mission Alignment") to reference the operator's specific values.

Once all eleven steps are done, write a first entry to `docs/.foundation_review_log.md`:

```
## YYYY-MM-DD — Initial bootstrap
Foundation files created via bootstrap interview. Next review due: YYYY-MM-DD (+30 days).
```

Then summarize the foundation to the operator and suggest they `git commit` the result.

---

# Foundation Review Protocol

Foundation files drift. Concepts get renamed in conversation but not in `domain_terminology.md`. Scope creeps into Phase 1 work even though the roadmap says Phase 2. Completed items linger as ⬜ in `project_plan.md`. The review protocol catches this.

## Manual trigger

**Trigger:** operator types `Review the foundation`.

1. Read every foundation file end-to-end.
2. Cross-check, looking specifically for:
   - **Conflicts** — two files say different things about the same concept.
   - **Drift** — vocabulary used in recent work (last 10 commits, recent open files) that doesn't appear in `domain_terminology.md`.
   - **Stale** — items marked ⬜ in `project_plan.md` that the codebase shows as already implemented.
   - **Gaps** — features mentioned in code or commits with no entry in `project_plan.md` or `user_journeys.md`.
3. Produce a report grouped under those four headings. Each finding cites the file(s) and the specific lines.
4. Propose specific edits — do NOT apply them yet. Wait for operator approval.
5. After approval, apply edits in order. Re-show the operator the diff if it touches `vision_and_mission.md`, `roadmap.md`, or `domain_terminology.md` (the locked layers).
6. Append a new entry to `docs/.foundation_review_log.md` with date, findings count, and a one-line summary.

## Automatic reminder

At the start of every session, after reading `CLAUDE.md`, also read `docs/.foundation_review_log.md`. Compute days since the most recent review entry's date. If > 30 days, output a single line to the operator before any other response:

```
↻ Foundation last reviewed YYYY-MM-DD (N days ago). Type "Review the foundation" when ready.
```

Do **not** block work. The reminder is informational. If the log file doesn't exist yet, do nothing (the bootstrap hasn't completed yet).

## Scheduled trigger (optional)

For a true time-based trigger, the operator can create a Claude Code routine via the `/schedule` skill:

```
/schedule create
Name:     foundation-review
Schedule: every Monday at 09:00
Prompt:   Review the foundation
```

This runs as a remote agent on the schedule and produces the review report automatically. The operator approves edits as usual.

---

# Vision & Mission Alignment

All work on this project must align with the values defined in `docs/vision_and_mission.md`. Before recommending or building anything, verify the proposal is consistent with those values. If it isn't, surface the conflict before continuing.

> Replace this paragraph after bootstrap with one sentence capturing the project's core principle — e.g., "Local-first, execution-only — no custody, no predictions, no centralized control."

---

# Product Development Workflow

All feature work follows this cycle. Recognize the trigger phrases below and respond accordingly.

## Phase 1 — Idea Intake

**Trigger:** `New idea: <description>`

Respond with a structured assessment:

- **Vision alignment** — does it fit `docs/vision_and_mission.md`?
- **Business value** — what does this add for the user?
- **Effort estimate** — S / M / L
- **Complexity** — Low / Medium / High
- **Recommendation** — Build now / Backlog / Park, with a short rationale

Do **NOT** modify any file at this stage. The operator decides next.

## Phase 2 — Backlog or Park

**Trigger:** `Add to backlog` → append to `docs/project_plan.md` under **Backlog** with date and one-line description.

**Trigger:** `Park this` → append to `docs/project_plan.md` under **Parked Items** with date and reason.

Confirm the update and show the appended line.

## Phase 3 — Planning

**Trigger:** `Let's build <item>`

Produce a full plan before writing any code:

1. **Goal** — one-sentence description
2. **Affected modules** — which files will be created or modified, and why
3. **Implementation steps** — numbered, ordered, granular enough to execute one at a time
4. **Tests** — exact test function names + what each covers, grouped by file
5. **Functional tests** — exact lines to be added to `docs/functional_tests.md`
6. **Architectural decisions** — any deviations from or additions to the existing architecture

Wait for explicit plan approval before writing any code.

## Phase 4 — Execution

**Trigger:** `Plan accepted`

Execute the approved plan:

- Write application code in the affected modules.
- Write test scripts.
- Run tests and confirm all new and existing tests pass.
- Append functional test entries (status: `open`) to `docs/functional_tests.md` and confirm which lines were added.
- Update `docs/project_plan.md`, `docs/architecture.md` if architecture changed, and `docs/testing/test_suite.md` if new tests were added.
- Do **NOT** commit or push. Wait for operator to test and provide feedback.

**Phase 4 completion checklist — MUST complete ALL before using the word "commit":**

```
[ ] Code written and compiles / tests pass
[ ] Functional test entries written in docs/functional_tests.md (status: open)
[ ] docs/project_plan.md updated
[ ] docs/architecture.md updated if architecture changed
[ ] docs/testing/test_suite.md updated if new tests added
[ ] Operator has tested locally and confirmed
```

Each conversational tweak during a feature build is still Phase 4 — Phase 5 applies at the end.

**Important — discuss before building.** When the operator asks a question, raises an idea, or identifies a potential issue, do NOT immediately write code. The process is: (1) discuss, (2) propose options, (3) wait for explicit approval, (4) only then build. Questions are not requests to code.

## Phase 5 — Functional Testing

After execution, append functional test entries (status: `open`) to `docs/functional_tests.md` as a direct file write — not a suggestion. Confirm which lines were added.

The operator runs the tests and updates statuses to `passed` or `failed`. Do not commit until the operator confirms.

## Phase 6 — Closing

**Trigger:** `Functional tests closed` or operator confirms tests pass.

Commit to a **feature branch** (not main) and push:

1. `git checkout -b feature/<short-name>`
2. `git commit -m "<descriptive message>"`
3. `git push -u origin feature/<short-name>`
4. The operator merges to main when ready.

Update documentation if not already done in Phase 4:
- `docs/project_plan.md` — mark item completed with date
- `docs/architecture.md` — update if changed
- `docs/testing/test_suite.md` — update if new tests added
- `docs/design/user_journeys.md` — check if a journey was added, changed, or extended; propose updates

---

# Session Hygiene

Long conversations cause context drift. Proactively suggest closing the session and starting fresh when:

- A major feature is complete and committed
- The session has exceeded ~3-4 hours of active work
- Multiple workflow steps have been skipped or corrected in the same session
- A heavy documentation sweep has just finished

Before closing a session:
1. Commit or note pending work
2. Save any new feedback to memory
3. Briefly summarize state so the next session picks up cleanly

---

# Next Step Suggestion

At the end of every turn where a task is completed (phase closed, commit made, or explicit "what's next?"), suggest a concrete next step based on the backlog in `docs/project_plan.md`. Format as a single short sentence the operator can accept or ignore. Example: "Next: let's build the X feature from the backlog."

---

# Documentation Files

| File | Purpose |
|---|---|
| `docs/vision_and_mission.md` | Why this project exists |
| `docs/roadmap.md` | Phased product roadmap |
| `docs/domain_terminology.md` | Locked canonical terms |
| `docs/non_goals.md` | What we explicitly will not build |
| `docs/architecture.md` | Technical architecture and decisions |
| `docs/project_plan.md` | Single source of truth for completed and pending work |
| `docs/functional_tests.md` | Open / passed / failed manual tests |
| `docs/testing/test_suite.md` | Automated test inventory |
| `docs/design/design_system.md` | Visual & accessibility rules |
| `docs/design/user_journeys.md` | Who does what, when |
| `docs/.foundation_review_log.md` | Audit trail of foundation reviews |
