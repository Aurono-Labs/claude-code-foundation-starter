# Project Conventions

<!-- BOOTSTRAP INSTRUCTIONS FOR CLAUDE CODE: read me at session start

This is the keystone file of one project's documentation foundation. It is
intentionally generic. The first time the operator runs this project through
Claude Code, walk them through the BOOTSTRAP PROTOCOL below. Until that is
done, treat this file as scaffolding, not a contract.

After bootstrap, remove this comment block and replace the placeholders
(`<...>`) with the operator's confirmed content.

END BOOTSTRAP -->

> **Status:** scaffold. Run `Bootstrap the project` to fill in.

## Canon Alignment

<Canon mode: replace this paragraph with the `Canon Alignment` block from the canon repo's `README.md`.
Single-project mode: delete this section. The project's values and design live in `docs/vision_and_mission.md` and `docs/design/design_system.md`.>

---

## Running & Installing

| Task | Command | Notes |
|---|---|---|
| Dev | `<dev command>` | |
| Install (production) | `<install command>` | |
| Build release artifact | `<build command>` | |

## Tests

| Suite | Command | When |
|---|---|---|
| Fast suite | `<fast test command>` | Default |
| Full suite | `<full test command>` | Touching the core |

## Git

- **Main branch**: `<main branch name>`
- **Feature branches**: short-lived, named `feature/<short-name>`, branched off main, merged through a pull request, deleted after merge.
- **Who commits where**: <who merges to main; whether others work through pull requests>. Check who you're working for with `gh api user --jq .login`.
- **Pre-commit hook** (recommended): block commits that touch user-facing code unless `docs/functional_tests.md` changes too. Bypass with `--no-verify` only for refactors with no visible change.

## Other repos

<List sibling repos this project works with: the canon, a website with support docs, a product this one forked from.>

- From this project's sessions, edit files in a sibling repo if needed, but **never commit, push or open pull requests there.** That happens from a session in that repo.
- An uncommitted edit in another repo can disappear (stashed, reset, overwritten). Say what you changed there, and check later that it landed.

---

# Bootstrap Protocol

**Trigger:** the operator types `Bootstrap the project`, or this is the first session and `docs/` still holds BOOTSTRAP blocks.

## Step 0: find the canon

Ask: **"Does your organization have a canon repo?"** Also look for one yourself: a sibling directory named `*-canon` with a `00-canon/` folder.

- **Canon mode** (a canon exists):
  1. Read the canon's `README.md`, `CLAUDE.md` and `00-canon/` before anything else.
  2. Replace the `Canon Alignment` placeholder above with the block from the canon's `README.md`.
  3. **Skip** `docs/vision_and_mission.md` and `docs/design/design_system.md`: replace each with a two-line pointer to the canon file. Ask only how this product lives up to each canon belief, and whether it needs any deliberate design exception.
  4. Start `docs/domain_terminology.md` from the canon's `05-terminology.md`: product terms go here, shared terms stay there.
  5. The workflow and release sections below follow the canon's `08` and `09` files: localize them, don't change their shape.
  6. At the end, **draft `01-products/<this-product>.md` in the canon repo** from the canon's `_template.md`, and a Snapshot row for its roadmap. Don't commit there; tell the operator to commit from a canon session.
- **Single-project mode** (no canon): run every file below as an interview. Tell the operator once, at the end: when a second project starts and you find yourself copying sections of this file into it, it's time for a canon (the starter's `canon/` folder, `04-process/extracting-a-canon.md`).

## Steps

For each file:

1. Read its BOOTSTRAP block for the shape the content should take.
2. Ask for existing material (a deck, a web page, a wiki, an earlier repo). Offer to read it.
3. Otherwise, run the interview prompts in the block.
4. **Never invent content.** If the operator can't answer a section, mark it `TODO` and move on.
5. Show the proposed content and wait for confirmation.
6. On confirmation, write the file and remove its BOOTSTRAP block.

**Order:**

1. `docs/vision_and_mission.md` (canon mode: pointer only)
2. `docs/roadmap.md`
3. `docs/domain_terminology.md`
4. `docs/non_goals.md`
5. `docs/architecture.md`
6. `docs/project_plan.md`, `docs/backlog.md`, `docs/project_history.md`
7. `docs/design/design_system.md` (canon mode: pointer plus exceptions)
8. `docs/design/user_journeys.md`
9. `docs/testing/test_suite.md`
10. `docs/functional_tests.md`
11. `docs/release_notes_next.md` (only if the project has staged releases)
12. **Finally:** this file. Fill in the commands, branch, people, other repos, and remove the sections that don't apply.

Then write the first entry of `docs/.foundation_review_log.md`:

```
## YYYY-MM-DD: Initial bootstrap
Foundation files created via bootstrap interview (canon mode / single-project mode). Next review due: YYYY-MM-DD (+30 days).
```

Summarize the foundation and suggest a commit.

---

# Foundation Review Protocol

**Trigger:** the operator types `Review the foundation`.

1. Read every foundation file end to end.
2. Look for:
   - **Conflicts**: two files say different things about the same concept.
   - **Drift**: words used in recent work (last commits, open files) that aren't in `domain_terminology.md`. In canon mode, also: values, design principles or workflow rules restated in this repo instead of pointed at.
   - **Stale**: open plan items the code shows as done; closed phases still in the plan instead of the history file.
   - **Gaps**: features in code or commits with no plan entry or journey.
   - **Unverified findings**: an open item that says something is broken or missing. Check it against the code before carrying it forward.
3. Report under those headings, each finding with file and line.
4. Propose edits; apply only after approval. Show the diff again for anything touching vision, roadmap or terminology.
5. Append to `docs/.foundation_review_log.md`: date, number of findings, one-line summary.

**Reminder:** at session start, read `docs/.foundation_review_log.md`. If the last review is more than 30 days old, say so in one line before anything else: `Foundation last reviewed YYYY-MM-DD (N days ago). Type "Review the foundation" when ready.` Don't block work. If the log doesn't exist, the bootstrap hasn't run; say nothing.

**Scheduled (optional):** create a recurring routine with `/schedule` whose prompt is `Review the foundation`.

---

# Vision & Mission Alignment

All work must align with <canon mode: `../<org>-canon/00-canon/01-values-and-vision.md` | single-project mode: `docs/vision_and_mission.md`>. Before recommending or building anything, check the proposal against it; if it conflicts, say so before continuing.

> Replace after bootstrap with one sentence that captures the project's core principle.

---

# Product Development Workflow

<Canon mode: add "The workflow below follows `<org>-canon/00-canon/08-development-workflow.md`." and keep the shape below.>

Recognize these trigger phrases and respond accordingly.

## Phase 1: Idea intake

**Trigger:** `New idea: <description>`

- **Vision alignment**: does it fit the values? Cite them; don't restate them.
- **User value**: what does it add, and for whom?
- **Effort**: S / M / L
- **Complexity**: Low / Medium / High
- **Recommendation**: build now, backlog or park, with a short reason

Do not modify any file in this phase.

## Phase 2: Backlog or park

**Trigger:** `Add to backlog` appends to `docs/backlog.md` with the date and a short description. `Park this` appends to its Parked section with the date and the reason. Show the appended lines.

## Phase 3: Planning

**Trigger:** `Let's build <item>`

1. **Goal**: one sentence
2. **Affected modules**: which files, and why
3. **Implementation steps**: numbered, small enough to execute one at a time
4. **Tests**: exact test names, grouped by file
5. **Functional tests**: exact entries for `docs/functional_tests.md`
6. **Canon or design check**: copy against tone and writing style, visuals against the design system and UX principles, new words against the glossary
7. **Architectural decisions**: deviations from or additions to the architecture

Wait for explicit approval before writing code. Split large work into phases, and merge each before starting the next.

## Phase 4: Execution

**Trigger:** `Plan accepted`

- Write the code and the tests; run the suite.
- Append functional test entries (status: `open`) to `docs/functional_tests.md`.
- Update `docs/project_plan.md`, `docs/architecture.md` if the architecture changed, `docs/testing/test_suite.md` if tests were added.
- **Don't deviate from the approved plan.** If a problem needs a deviation, or the plan turns out unsafe, stop and present it.
- **Verify with real data.** Pull evidence from the dev database or running instance yourself rather than asking the operator to check. Check claims made by tools or other models against the data before recording them.
- Do **not** commit or push. Wait for the operator to test.

**Completion checklist, all done before the word "commit" appears:**

```
[ ] Code written; tests pass
[ ] Functional test entries written (status: open)
[ ] docs/project_plan.md updated
[ ] docs/architecture.md updated if the architecture changed
[ ] docs/testing/test_suite.md updated if tests were added
[ ] Operator has tested locally and confirmed
```

Every tweak during a build is still Phase 4.

**Discuss before building.** A question, an idea or a reported issue is not a request to code: discuss, propose options, wait for approval, then build.

## Phase 5: Functional testing

The operator runs the open entries and marks them `passed` or `failed`. Claude may run and close entries that need no human eyes (backend behavior provable by tests and API calls); entries that need a browser, a device or judgment stay open.

The functional test log is historical: when behavior changes later, add entries; never rewrite old ones.

## Phase 6: Closing

**Trigger:** `Functional tests closed`, or the operator confirms.

1. `git checkout -b feature/<short-name>`, commit, `git push -u origin feature/<short-name>`, open a pull request. Docs and functional tests ride in the same pull request; no docs-only branches.
2. Mark the plan item done with the date. When it closes the last open item of a phase, move that phase to `docs/project_history.md`.
3. Update architecture, test inventory, and user journeys if one changed.
4. **Sibling check:** if this project forked, or was forked from, another repo's code, does this change apply there? Add it to that repo's backlog.
5. **Support-docs check:** if user-facing docs live elsewhere, do they now describe old behavior?
6. **Canon drift check** (canon mode): a deliberate deviation from canon gets a proposed line for the canon's product page; accidental drift gets a fix.
7. If the work taught a rule worth keeping, propose it for this file, or for the canon if it holds for every project.

---

# Release Workflow

<Delete this section if the project has no staged deployment. Canon mode: add "Releases follow `<org>-canon/00-canon/09-release-workflow.md`." and keep only the local detail below.>

| Stage | Where | Local detail |
|---|---|---|
| 1. Dev | `<dev machine>` | Tests green, merged, note in `docs/release_notes_next.md` |
| 2. Pre-release | `<acceptance host>` | Audit notes against the last promoted tag, tag, publish as pre-release, soak |
| 3. Promote | `<production host>` | Mark latest, deploy the same artifact, health checks, clear the notes file |

Never re-tag a failed attempt; bump to the next pre-release version. Never deploy to a real environment automatically: give the commands, the operator runs them. If the operator says "ship it" during Stage 1, ask which stage they mean.

---

# Dependency Security

<Keep and localize, or delete for projects without third-party packages.>

1. **Justify every new package.** Could we write the twenty lines ourselves? Every dependency is attack surface.
2. **Check it**: maintainers, last commit, depth of its dependency tree. A single-maintainer package with a deep tree is high risk.
3. **Lock with hashes**, and regenerate the lock after every change: `<lock command>`.
4. **Keep runtime and dev dependencies separate.**
5. **Audit before every release**: `<audit commands>`. Install from the lock only (`--require-hashes`, `npm ci` or equivalent).

---

# Session Hygiene

Suggest a fresh session when a major feature is committed, after three to four hours of work, after several workflow steps were skipped or corrected, or after a heavy documentation sweep. The rules in this file and in memory load cleanly at session start and fade in a long session.

Before closing: commit or note pending work, save new feedback to memory, summarize the state for the next session.

**Memory versus files:** memory holds how the operator likes to work. A rule that holds for the whole project belongs in this file; one that holds for every project belongs in the canon. When a memory turns into a rule, move it and point the memory at the file.

---

# Next Step Suggestion

At the end of every turn that completes a task, suggest one concrete next step from `docs/backlog.md` or the open plan items, in one sentence the operator can accept or ignore.

---

# Documentation Files

| File | Purpose |
|---|---|
| `docs/vision_and_mission.md` | Why this project exists (canon mode: pointer) |
| `docs/roadmap.md` | Phased product roadmap |
| `docs/domain_terminology.md` | Locked product terms |
| `docs/non_goals.md` | What we explicitly won't build |
| `docs/architecture.md` | Technical architecture and decisions |
| `docs/project_plan.md` | What's being built: open phases and items |
| `docs/backlog.md` | What might be built, and what was parked with the reason |
| `docs/project_history.md` | Closed phases, moved out of the plan |
| `docs/functional_tests.md` | Open, passed and failed manual tests |
| `docs/testing/test_suite.md` | Automated test inventory |
| `docs/design/design_system.md` | Visual and accessibility rules (canon mode: pointer plus exceptions) |
| `docs/design/user_journeys.md` | Who does what, when |
| `docs/release_notes_next.md` | Notes for the next release (staged releases only) |
| `docs/.foundation_review_log.md` | Record of foundation reviews |
