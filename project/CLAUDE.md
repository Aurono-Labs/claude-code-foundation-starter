# Project Conventions

> **Status: scaffold, not bootstrapped yet.** At the start of a session, if any file in `docs/` still holds a BOOTSTRAP comment block, say in one line that the foundation isn't filled in and offer `Bootstrap the project`. Until it has run, treat this file as scaffolding, not a contract. The bootstrap deletes this status line.

## Canon Alignment

The bootstrap replaces this whole section, heading included, with the `Canon Alignment` block from `../<org>-canon/README.md`. In single-project mode it deletes this section.

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
- **Remote**: <remote and host, e.g. `origin` on GitHub, or none>
- **Feature branches**: short-lived, named `feature/<short-name>`, branched off main, deleted after merge.
- **Who merges**: <solo: "I merge my own branches" | team: who merges to main, and that others work through pull requests>. Check who you're working for with `gh api user --jq .login`.
- **Pre-commit hook**: blocks commits that touch user-facing code (<paths>) unless `docs/functional_tests.md` changes too. Bypass with `--no-verify` only for refactors with no visible change.
- **Deploying**: never deploy to a real environment automatically. Give the commands; the operator runs them.

## Other repos

<List sibling repos this project works with: the canon, a website with support docs, a project this one forked from.>

- From this project's sessions, edit files in a sibling repo if needed, but **never commit, push or open pull requests there.** That happens from a session in that repo.
- An uncommitted edit in another repo can disappear (stashed, reset, overwritten). Say what you changed there, and check later that it landed.

---

# Bootstrap Protocol

**Trigger:** the operator types `Bootstrap the project`.

This section is the one-time setup. Its last step deletes it; the starter pack keeps the original if a file ever needs to be bootstrapped again.

## Step 0: three questions up front

Ask these once, before any file:

1. **"Do you have existing material: a deck, a web page, a wiki, an earlier repo?"** Read whatever is shared, and use it for every file below instead of asking per file.
2. **"Do you work on this alone, or with others?"** When alone, skip interview prompts marked *(team)* and the questions about reviewers and pull requests.
3. **"Does your organization have a canon repo?"** Also look yourself: a sibling directory (`../*-canon`) with a `00-canon/` folder.

### Canon mode (a canon exists)

1. Read `../<org>-canon/README.md`, `../<org>-canon/CLAUDE.md` and every file in `../<org>-canon/00-canon/`.
2. **Check that the canon is finished.** List the files in `../<org>-canon/00-canon/` and `../<org>-canon/02-roadmap/` that still hold a BOOTSTRAP comment block and tell the operator which ones are empty. Don't run the canon's own bootstrap from here; that happens in a session in the canon repo. Carry on, and mark every point that depends on an empty canon file `TODO: canon file <name> is not filled in yet`.
3. Replace this file's `Canon Alignment` section, heading included, with the block from the canon's `README.md`.
4. `docs/vision_and_mission.md` and `docs/design/design_system.md` become pointers (their BOOTSTRAP blocks say how). Ask only how this project lives up to each canon belief, whether it needs any deliberate design exception, and where it will keep its copy of the design tokens.
5. `docs/domain_terminology.md` points at `../<org>-canon/00-canon/05-terminology.md` and holds only this project's own words. Never copy or redefine a canon term.
6. The workflow and release sections below keep their shape. Lines starting with *(canon mode)* stay; lines starting with *(single-project mode)* go.
7. **Draft in the canon repo, without committing there:**
   - `../<org>-canon/01-products/<this-project>.md`, from `../<org>-canon/01-products/_template.md`. Ask for the repo owner and whether the repo is private or public.
   - this project's row in the per-product table of `../<org>-canon/00-canon/01-values-and-vision.md` (the belief answers from point 4);
   - its row in the "Where products keep their copy" table of `../<org>-canon/00-canon/02-design-system.md`;
   - its Snapshot row in `../<org>-canon/02-roadmap/portfolio-roadmap.md`.

### Single-project mode (no canon)

Run every file below as an interview. Lines starting with *(canon mode)* go; lines starting with *(single-project mode)* stay.

## Steps

For each file, in the order below:

1. Read its BOOTSTRAP block for the interview prompts and the shape the content should take.
2. Use the material from Step 0, and every answer already given for an earlier file, first. Ask a prompt only for what isn't answered yet; skip a file's "existing material" prompt entirely.
3. **Never invent content.** If the operator can't answer something, write `TODO: <what's missing>` in its place and move on.
4. Show the proposed content and wait for confirmation.
5. On confirmation, **replace the whole file** with the confirmed content. Nothing of the scaffold stays: not the BOOTSTRAP block, not the "Run `Bootstrap`" status line, not the "go here" comments, not the sample entries.

Files marked *no interview* only get their scaffold replaced by an empty, ready-to-use version.

**Order:**

1. `docs/vision_and_mission.md` (canon mode: pointer)
2. `docs/roadmap.md`
3. `docs/domain_terminology.md`
4. `docs/non_goals.md`
5. `docs/architecture.md`
6. `docs/project_plan.md` and `docs/backlog.md`
7. `docs/project_history.md` (no interview)
8. `docs/design/design_system.md` (canon mode: pointer plus exceptions)
9. `docs/design/user_journeys.md`
10. `docs/testing/test_suite.md`
11. `docs/functional_tests.md` (no interview)
12. **This file**, through the interview below.

## Step 12: this file

Ask, and check what can be checked:

1. **Commands**: dev, install, fast tests, full tests. Build release artifact only if there is one.
2. **Main branch**: compare the answer with `git branch --show-current` and point out a difference.
3. **Remote**: is there one (check `git remote -v`), and on which host? Without a remote, Phase 6 merges locally.
4. *(team)* **Who merges to main**, and whether others work through pull requests.
5. **Other repos** this project works with (canon, a website with support docs, a project it forked from).
6. **Staged releases**: does a change go to a test or acceptance environment before production? If yes: the hostnames of each stage.
7. **Dependencies**: are third-party packages used? If yes: the lock and audit commands.
8. **Pre-commit hook**: install it now? If yes, ask which paths hold user-facing code, put them in `scripts/pre-commit` as its `USER_FACING` pattern, copy that file to `.git/hooks/pre-commit`, make it executable, and say so. If no, delete `scripts/pre-commit` and the hook line in the Git section.
9. **Core principle**: single-project mode: one sentence, from `docs/vision_and_mission.md`. Canon mode: cite the canon belief numbers this project leans on most; don't paraphrase them.

Then clean up this file:

- Fill every `<...>` placeholder in every section of this file except this protocol, which gets deleted. Placeholders inside trigger phrases and examples (`feature/<short-name>`, `New idea: <description>`, `Let's build <item>`) are syntax and stay.
- A line or list item that starts with *(canon mode)* or *(single-project mode)* belongs to that mode only. Delete the ones for the other mode, whole; remove the marker from the ones that stay.
- No other repos: delete the **Other repos** section.
- No staged releases: delete the **Release Workflow** section, `docs/release_notes_next.md`, and its row in the Documentation Files table. Staged releases: keep `docs/release_notes_next.md` as it is; it's ready to use.
- No third-party packages: delete the **Dependency Security** section.
- Delete the status line at the top.
- Write the first entry of `docs/.foundation_review_log.md`, in the same shape every review uses:

  ```
  ## YYYY-MM-DD: Initial bootstrap (canon mode | single-project mode)
  Findings: 0. Open TODOs: <n>. Next review due: YYYY-MM-DD (+30 days).
  ```

- **Last, delete this whole Bootstrap Protocol section.**

## Closing summary

Tell the operator:

- what was written, and every `TODO:` left, with its file;
- *(canon mode)* which canon files were drafted, that they are not committed, and that they should be committed from a session in the canon repo;
- *(single-project mode)* that when a second project starts and sections of this file get copied into it, it's time for a canon (the starter pack's `canon/` folder and its `04-process/extracting-a-canon.md`);
- the suggested commit.

---

# Foundation Review Protocol

**Trigger:** the operator types `Review the foundation`.

1. Read every foundation file end to end.
2. Look for:
   - **Conflicts**: two files say different things about the same concept.
   - **Drift**: words used in recent work (last commits, open files) that aren't in `docs/domain_terminology.md`.
   - *(canon mode)* **Canon drift**: values, design principles or workflow rules restated in this repo instead of pointed at.
   - **Stale**: open plan items the code shows as done; closed phases still in the plan instead of `docs/project_history.md`.
   - **Gaps**: features in code or commits with no plan entry or journey.
   - **TODOs**: every `TODO:` left in the docs. Can one be answered now?
   - **Unverified findings**: an open item that says something is broken or missing. Check it against the code before carrying it forward.
3. Report under those headings, each finding with file and line.
4. Propose edits; apply only after approval. Show the diff again for anything touching vision, roadmap or terminology.
5. Append to `docs/.foundation_review_log.md`, in the same shape as the bootstrap entry: date, number of findings, open TODOs, next review due.

**Reminder:** at session start, read `docs/.foundation_review_log.md` (if it doesn't exist, the bootstrap hasn't run; skip this). If the date of its most recent entry is more than 30 days ago, say so in one line before anything else: `Foundation last reviewed YYYY-MM-DD (N days ago). Type "Review the foundation" when ready.` Don't block work.

**Scheduled (optional):** create a recurring routine with `/schedule` whose prompt is `Review the foundation`.

---

# Vision & Mission Alignment

All work must align with the values in:

*(single-project mode)* `docs/vision_and_mission.md`

*(canon mode)* `../<org>-canon/00-canon/01-values-and-vision.md`

Before recommending or building anything, check the proposal against them; if it conflicts, say so before continuing.

Core principle: <filled in by Step 12, point 9>

---

# Product Development Workflow

*(canon mode)* The workflow below follows `../<org>-canon/00-canon/08-development-workflow.md`.

Recognize these trigger phrases and respond accordingly. (The workflow's Phases 1 to 6 are steps in building one change; they are not the numbered phases of `docs/project_plan.md` or `docs/roadmap.md`.)

## Phase 1: Idea intake

**Trigger:** `New idea: <description>`

- **Vision alignment**: does it fit the values? Cite them; don't restate them.
- **User value**: what does it add, and for whom?
- **Effort**: S / M / L
- **Complexity**: Low / Medium / High
- **Recommendation**: build now, backlog or park, with a short reason

Do not modify any file in this phase.

## Phase 2: Backlog or park

**Trigger:** `Add to backlog` appends to `docs/backlog.md`: the date, who raised it, a short description. `Park this` appends to its Parked section with the date and the reason. Show the appended lines.

## Phase 3: Planning

**Trigger:** `Let's build <item>`

1. **Goal**: one sentence
2. **Affected modules**: which files, and why
3. **Implementation steps**: numbered, small enough to execute one at a time
4. **Tests**: exact test names, grouped by file
5. **Functional tests**: exact entries for `docs/functional_tests.md`
6. **Design and copy check**: visuals against `docs/design/design_system.md`, new words against `docs/domain_terminology.md`.
   - *(canon mode)* Also against the canon's design system, UX principles, tone of voice and writing style.
7. **Architectural decisions**: deviations from or additions to the architecture

Wait for explicit approval before writing code. Split large work into parts, and merge each before starting the next.

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

1. `git checkout -b feature/<short-name>` and commit. Docs and functional tests ride in the same commit or pull request as the code; no docs-only branches.
   - With a remote: `git push -u origin feature/<short-name>` and open a pull request; whoever the Git section names merges it.
   - Without a remote: the operator merges the branch into main locally when ready.
2. Mark the plan item done with the date. When it closes the last open item of a plan phase, move that phase to `docs/project_history.md`.
3. Update architecture, test inventory, and user journeys if one changed.
4. **Sibling check:** if this project forked, or was forked from, another repo's code, does this change apply there? Add it to that repo's backlog.
5. **Support-docs check:** if user-facing docs live elsewhere, do they now describe old behavior?
6. *(canon mode)* **Canon drift check:** a deliberate deviation from canon gets a proposed line for `../<org>-canon/01-products/<this-project>.md`; accidental drift gets a fix.
7. If the work taught a rule worth keeping, propose it for this file.
8. *(canon mode)* If that rule holds for every project, propose it for the canon instead.

---

# Release Workflow

*(canon mode)* Releases follow `../<org>-canon/00-canon/09-release-workflow.md`. This section holds only this project's stages; the rules live there.

| Stage | Where | What happens |
|---|---|---|
| 1. Dev | `<dev machine>` | Tests green, merged, a note in `docs/release_notes_next.md` |
| 2. Pre-release | `<acceptance host>` | Audit the notes, tag, publish as pre-release, deploy, soak |
| 3. Promote | `<production host>` | Mark latest, deploy the same artifact, health checks, clear the notes file |

*(single-project mode)* The rules:

- *(single-project mode)* Before tagging, audit `docs/release_notes_next.md` against the last tag that reached production: drop what already shipped, add every user-visible change since. After a failed soak, audit against that same tag again, never against the abandoned pre-release.
- *(single-project mode)* A fix for something the soak found gets its own release note.
- *(single-project mode)* Tags are immutable: after a failed soak, bump to the next pre-release version; never re-tag.
- *(single-project mode)* If the operator says "ship it" during Stage 1, ask which stage they mean.

---

# Dependency Security

1. **Justify every new package.** Could we write the twenty lines ourselves? Every dependency is attack surface.
2. **Check it**: maintainers, last commit, depth of its dependency tree. A single-maintainer package with a deep tree is high risk.
3. **Lock with hashes**, and regenerate the lock after every change: `<lock command>`.
4. **Keep runtime and dev dependencies separate.**
5. **Audit before every deploy**: `<audit commands>`. Install from the lock only (`--require-hashes`, `npm ci` or equivalent).

---

# Session Hygiene

Suggest a fresh session when a major feature is committed, after three to four hours of work, after several workflow steps were skipped or corrected, or after a heavy documentation sweep. The rules in this file and in memory load cleanly at session start and fade in a long session.

Before closing: commit or note pending work, save new feedback to memory, summarize the state for the next session.

**Memory versus files:** memory holds how the operator likes to work. A rule that holds for the whole project belongs in this file. When a memory turns into a rule, move it and point the memory at the file.

*(canon mode)* A rule that holds for every project belongs in the canon.

---

# Next Step Suggestion

At the end of every turn that completes a task, suggest one concrete next step from `docs/backlog.md` or the open plan items, in one sentence the operator can accept or ignore.

---

# Documentation Files

| File | Purpose |
|---|---|
| `docs/vision_and_mission.md` | Why this project exists (in canon mode, a pointer to the canon) |
| `docs/roadmap.md` | Phased product roadmap |
| `docs/domain_terminology.md` | Locked project terms |
| `docs/non_goals.md` | What we explicitly won't build |
| `docs/architecture.md` | Technical architecture and decisions |
| `docs/project_plan.md` | What's being built: open phases and items |
| `docs/backlog.md` | What might be built, and what was parked with the reason |
| `docs/project_history.md` | Closed phases, moved out of the plan |
| `docs/functional_tests.md` | Open, passed and failed manual tests |
| `docs/testing/test_suite.md` | Automated test inventory |
| `docs/design/design_system.md` | Visual and accessibility rules (in canon mode, a pointer plus this project's exceptions) |
| `docs/design/user_journeys.md` | Who does what, when |
| `docs/release_notes_next.md` | Notes for the next release |
| `docs/.foundation_review_log.md` | Record of the bootstrap and every review |
