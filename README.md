# Claude Code Foundation Starter Pack

> Created by **Aurono Labs** · [auronolabs.com](https://auronolabs.com)
> A working method, codified.

A skeleton for starting a new project with Claude Code in a structured way. Instead of opening a fresh repo and immediately asking Claude Code to write features, you drop these files in, run a short bootstrap interview, and end up with a documentation foundation Claude Code re-anchors on every session.

The method behind this pack is described in detail in the companion talk *How I Code With Claude Code*. Every foundation file's bootstrap preamble includes a short **"Example — how Aurono Labs answered this"** block drawn from the real Aurono Start documentation, so operators can see the shape and quality bar of a good answer before they start their interview.

---

## What's in this pack

```
.
├── CLAUDE.md                          ← Keystone: the contract
├── docs/
│   ├── vision_and_mission.md          ← Layer 1 — Why we exist
│   ├── roadmap.md                     ← Layer 2 — What we're shipping
│   ├── domain_terminology.md          ← Layer 3a — How we speak
│   ├── non_goals.md                   ← Layer 3b — What we explicitly won't do
│   ├── architecture.md                ← Layer 4a — Technical structure
│   ├── project_plan.md                ← Layer 4b — Single source of truth for work state
│   ├── functional_tests.md            ← Layer 5a — Manual / exploratory tests
│   ├── design/
│   │   ├── design_system.md           ← Layer 5b — Visual & accessibility rules
│   │   └── user_journeys.md           ← Layer 5c — Who does what, when
│   └── testing/
│       └── test_suite.md              ← Layer 5d — Automated test inventory
```

Each file is **deliberately empty** below a `<!-- BOOTSTRAP INSTRUCTIONS -->` block. The block tells Claude Code how to interview you and fill the file in. Nothing about your specific organization is prescribed — only the *shape* of the answers.

---

## How to use it

### Step 1 — Drop the pack into a fresh repo

```bash
# from the repo root
cp -R path/to/starter-pack/* .
git add -A && git commit -m "chore: add foundation skeleton"
```

### Step 2 — Open Claude Code in that repo

```bash
claude
```

Claude Code will read `CLAUDE.md` at session start. The CLAUDE.md in this pack contains the bootstrap protocol.

### Step 3 — Run the bootstrap interview

Type:

```
Bootstrap the foundation
```

Claude Code will walk through each file in order:

1. `vision_and_mission.md`
2. `roadmap.md`
3. `domain_terminology.md`
4. `non_goals.md`
5. `architecture.md`
6. `project_plan.md`
7. `design/design_system.md`
8. `design/user_journeys.md`
9. `testing/test_suite.md`
10. `functional_tests.md`

For each file it will ask you to either:
- Share existing material (PDFs, slides, web pages, internal wikis)
- Or answer the interview questions directly

After each file, it will write the file and confirm with you before moving on.

**Expect this to take 1.5 – 2.5 hours.** It is the most valuable two hours you will spend on the project.

### Step 4 — Start working

Once the foundation is in place, daily work follows the 6-phase workflow defined in `CLAUDE.md`:

```
"New idea: …"             →  Phase 1 — Idea Intake (assessment)
"Add to backlog"          →  Phase 2 — Backlog
"Let's build X"           →  Phase 3 — Planning
"Plan accepted"           →  Phase 4 — Execution (code + tests + docs, no commit)
(you test manually)       →  Phase 5 — Functional Testing
"Functional tests closed" →  Phase 6 — Closing (feature branch + commit + push)
```

---

## Keeping the foundation alive

Foundation files drift as the project grows. Two mechanisms in this pack keep them aligned:

### Manual review — anytime

```
Review the foundation
```

Claude Code reads every foundation file, looks for contradictions, vocabulary drift, scope creep, and stale completed items, and produces a report grouped by **Conflicts / Drift / Stale / Suggestions**. You approve, it applies edits, it logs the review in `docs/.foundation_review_log.md`.

### Automatic reminder — on session start

`CLAUDE.md` includes an instruction telling Claude Code to check `docs/.foundation_review_log.md` at session start and surface a one-line reminder if the last review is older than 30 days. Non-blocking — just a nudge.

### True scheduled trigger — optional

For a real time-based trigger, use Claude Code's `/schedule` skill to create a recurring routine:

```
/schedule create

Name:     foundation-review
Schedule: every Monday at 09:00
Prompt:   Review the foundation
```

This runs as a remote agent on the schedule you set. See the Claude Code docs on **routines** for setup.

---

## A note on the bootstrap preambles

Every file in this pack opens with an HTML-style `<!-- BOOTSTRAP -->` comment block. That block:

- Is **invisible** in rendered markdown (GitHub, editors)
- Is **visible** to Claude Code when it reads the file
- Tells Claude Code exactly how to interview you and what shape the final content should take
- Should be **deleted by Claude Code** once the file is filled, replaced with the synthesized content

If you ever want to rerun the interview for a single file, paste the preamble back at the top and ask Claude Code to re-bootstrap that file.

---

---

## About Aurono Labs

**Aurono Labs** is an organization building local-first, execution-only infrastructure for personal capital. The belief: if software can move money, it must be locally controlled, fully inspectable, and incentive-aligned — anything else eventually breaks trust.

Aurono Labs ships products under the Aurono name. **Aurono Start** is the first — a local-first, execution-only crypto trading application that runs on the user's own hardware, executes user-defined rules, and never takes custody of funds. Future phases extend the platform to portfolio-aware execution, community strategies, multi-asset support, and embeddable execution infrastructure.

This starter pack codifies the working method developed while building Aurono Start. The Aurono Start repository is the reference implementation of that method and the source of every example in this pack.

- Website: [auronolabs.com](https://auronolabs.com)
- Support docs: [support.auronolabs.com](https://support.auronolabs.com)
- Contact: eppo@auronolabs.com

## License

Licensed under the **Aurono Labs Foundation Starter License v1.0** — see [`LICENSE`](LICENSE) for the full text.

In short:

- **You can** use, copy, modify, and adapt this pack for your own projects — personal, internal, commercial, or open source. Projects you build with it are yours.
- **You can** share private copies with collaborators working with you on those projects.
- **You cannot** sell or commercialize this pack itself as a product, template, course, consulting deliverable, or paid offering.
- **You cannot** redistribute this pack publicly without prior written permission.

Commercial licensing or permission requests: **eppo@auronolabs.com**.
