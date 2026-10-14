# Claude Code Foundation Starter Pack

> Created by **Aurono Labs** · [auronolabs.com](https://auronolabs.com)
> A working method, codified.

A skeleton for starting a new project with Claude Code in a structured way. Instead of opening a fresh repo and immediately asking Claude Code to write features, you drop these files in, run a short bootstrap interview, and end up with a documentation foundation Claude Code re-anchors on every session.

The method behind this pack is described in the companion talk *How I Code With Claude Code*; the deck (HTML and PDF, Dutch and English) lives in [`presentation/`](presentation/). It covers the single-project method; the canon layer was added after the talk. Several project files include an **"Example: how Aurono Labs answered this"** block drawn from the Aurono Start documentation, so you can see the shape and quality bar of a good answer before your interview.

---

## Two layers

The pack has two templates. Start with the one you need now.

| | `project/` | `canon/` |
|---|---|---|
| **What it is** | The foundation for one project | The shared layer above several projects |
| **Holds** | Roadmap, terminology, architecture, plan, backlog, tests, journeys, the six-phase workflow | Values and vision, design system, UX principles, tone of voice, shared terminology, naming, writing style, the development and release workflows, one page per product, the portfolio roadmap |
| **You need it** | From the first commit | From the second project |
| **Bootstrap** | `Bootstrap the project` | `Bootstrap the canon` |

**Why a canon.** One project with a good foundation works. Two or three projects each with their own foundation drift apart: each writes its own vision text, design principles and workflow notes, nobody disagrees, and a year later they say different things. The canon holds the shared content once. Each project's `CLAUDE.md` points at it instead of restating it, and logs on purpose where it differs.

**When to add one.** The signal is copying: a section of one project's `CLAUDE.md` pasted into another, or the same fix applied by hand to two copies of one rule.

```
.
├── project/                            ← one per project
│   ├── CLAUDE.md                       ← keystone: workflow, bootstrap, review
│   └── docs/
│       ├── vision_and_mission.md       ← single-project mode only; canon mode points at the canon
│       ├── roadmap.md
│       ├── domain_terminology.md       ← this project's own words
│       ├── non_goals.md
│       ├── architecture.md
│       ├── project_plan.md             ← what's being built
│       ├── backlog.md                  ← what might be built, and what was parked
│       ├── project_history.md          ← closed phases
│       ├── functional_tests.md
│       ├── release_notes_next.md       ← only with staged releases
│       ├── design/
│       │   ├── design_system.md        ← canon mode: pointer plus exceptions
│       │   └── user_journeys.md
│       └── testing/
│           └── test_suite.md
├── canon/                              ← one per organization
│   ├── CLAUDE.md                       ← issues as inbox, files as record, cross-repo rules, review
│   ├── README.md                       ← includes the Canon Alignment block for projects
│   ├── 00-canon/                       ← values, design, UX, tone, terms, naming, style, workflows
│   ├── 01-products/_template.md        ← per project: deliberate adaptations, drift log
│   ├── 02-roadmap/portfolio-roadmap.md
│   ├── 03-conflicts/conflict-log.md
│   ├── 04-process/                     ← proposing a change, sync checklist, extracting a canon
│   └── 05-business/                    ← optional
├── presentation/                       ← the companion talk
└── LICENSE
```

Files that need your answers are empty below a `<!-- BOOTSTRAP INSTRUCTIONS -->` block that tells Claude Code how to interview you. The two workflow files in `canon/00-canon/` come filled in: they are the method itself.

---

## How to use it

### One project, no canon

```bash
cp -R path/to/starter/project/. my-project/
cd my-project && git add -A && git commit -m "Add foundation skeleton"
claude
```

Then type `Bootstrap the project`. Claude Code asks whether there's a canon, finds none, and walks through each file: share existing material or answer the interview. Expect 1.5 to 2.5 hours. It is the most valuable two hours you will spend on the project.

### Several projects, with a canon

Clone every repo as a sibling under one parent directory; the files reference each other by relative path.

```
work/
├── my-org-canon/        ← from starter/canon/
├── project-a/           ← from starter/project/
└── project-b/
```

1. **Create the canon.** Copy `canon/` into a new repo named `<org>-canon` and run `Bootstrap the canon`. If projects already exist, it runs `04-process/extracting-a-canon.md` instead: it reads the existing repos, lists where they disagree, and you decide each point.
2. **Connect each project.** In the project, run `Bootstrap the project`. It finds the canon, skips the interviews the canon already answers, pastes the `Canon Alignment` block into the project's `CLAUDE.md`, and drafts the project's page in `01-products/`. Commit that page from a canon session.
3. **Work.** Daily work follows the six-phase workflow below. Changes to shared content go through `canon/04-process/proposing-a-change.md`.

### Daily work: the six phases

```
"New idea: …"             →  Phase 1  assessment against the values, no file changes
"Add to backlog"          →  Phase 2  dated entry in docs/backlog.md
"Let's build X"           →  Phase 3  full plan, including a canon check
"Plan accepted"           →  Phase 4  code, tests, docs; no commit
(you test)                →  Phase 5  functional tests closed
"Functional tests closed" →  Phase 6  feature branch, pull request, sibling and drift checks
```

Projects with staged deployments add a three-stage release workflow: dev, pre-release on an acceptance environment, promote to production.

---

## What's new in this version

Learned from running the method across several projects at once:

- **The canon layer**, with a protocol for extracting one from repos that already exist.
- **Backlog and history** split out of the project plan, so the plan only shows what's open.
- **Phase 6 checks**: sibling repos that share code, support docs that live elsewhere, drift from canon. Docs ride in the feature pull request.
- **A release workflow**: audit the notes against the last promoted tag, never re-tag, never deploy automatically.
- **Verification rules**: check claims against real data, re-verify a finding before restating it, check a review against the repo rather than its summary.
- **Cross-repo rules**: edit in another repo but never commit there, and check later that the edit landed.
- **Working with more than one person**: issues as the inbox, files as the record, a **Not decided:** line on every open thread.
- **Dependency security**: justify, lock with hashes, audit before release.

---

## Keeping the foundation alive

- **`Review the foundation`** in a project: conflicts, drift, stale items, gaps and unverified findings, as a report you approve before anything changes. Logged in `docs/.foundation_review_log.md`; Claude reminds you at session start once the last review is more than 30 days old.
- **`Review the canon`** in the canon: projects drifting from canon, and canon's own pages about projects going stale. Each project's row is re-checked against its repo and dated.
- **Scheduled**: either review can run as a routine through Claude Code's `/schedule` skill.

---

## A note on the bootstrap blocks

Every file to be filled opens with an HTML-style `<!-- BOOTSTRAP -->` comment. It is invisible in rendered markdown, visible to Claude Code, says how to interview you and what shape the content should take, and is deleted once the file is filled. To rerun the interview for one file, paste its block back at the top and ask Claude Code to re-bootstrap that file.

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
