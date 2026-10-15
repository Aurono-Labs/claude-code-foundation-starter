# <Organization> canon: instructions for Claude

> **Status: scaffold, not bootstrapped yet.** At the start of a session, if any file in `00-canon/` or `02-roadmap/` still holds a BOOTSTRAP comment block, say in one line that the canon isn't filled in and offer `Bootstrap the canon`. Until it has run, treat this file as scaffolding. The bootstrap fills in every `<...>` placeholder below and deletes this status line.

This repo is <Organization>'s single source of truth for what its products share. Read `README.md` first for the structure and current status.

People who work here: <name> (<role>, decides on canon changes), <name> (<role>). Each works through Claude Code, locally or in a cloud session.

## Where things go

| What | Where |
|---|---|
| An action: someone does something, ideally by a date | An issue in this repo's tracker |
| A raw idea, not discussed yet | An issue with the `idea` label |
| A question that needs a decision | An issue with the `decision` label |
| A business-model thread with its reasoning | `05-business/open-discussions.md` (optional folder) |
| A product idea or a sequencing question | `02-roadmap/portfolio-roadmap.md`, plus the product's page in `01-products/` |
| A change to values, vision, design, tone, terminology, naming or a shared workflow | The matching `00-canon/*.md` file, following `04-process/proposing-a-change.md` |

Issues are the inbox, canon files are the record. When an `idea` or `decision` issue is settled, write the outcome into the right file, link the commit in the issue, and close the issue. A decision that only lives in an issue comment isn't recorded yet.

Don't keep action lists or to-do checkboxes in files here: a file can't assign anyone or notify anyone.

## Issues

- Title: what gets done, starting with a verb ("Ask the accountant what a holding costs to set up").
- One assignee, the person who does it.
- Labels: one or more area labels (`<area>`, `<area>`), plus `idea`, `decision` or `waiting` when one applies.
- Link the canon file an issue is about, so the next reader doesn't have to search.
- A due date goes on the first line of the body ("Due: YYYY-MM-DD").

If you use GitHub: `gh api` (REST) works both locally and in cloud sessions. `gh issue` and `gh project` use GraphQL, which some cloud sessions block.

```bash
gh api repos/<owner>/<repo>/issues -f title="..." -f body="..." \
  -f "assignees[]=<login>" -f "labels[]=<area>"
gh api repos/<owner>/<repo>/issues/<n>/comments -f body="..."
gh api -X PATCH repos/<owner>/<repo>/issues/<n> -f state=closed
```

## Changing files

- The decision owner (<login>) commits to `<main branch>` directly from a local session. Anyone else works on a branch and opens a pull request, which the decision owner merges. Check who you're working for with `gh api user --jq .login`.
- A cloud session can usually only push its own branch, so work there ends in a pull request.
- One topic per commit. Say what changed and why it matters.
- When a change makes something in `README.md` untrue, update `README.md` in the same commit.

## The product repos

The product repos are separate repos, cloned as siblings of this one (`../<product-repo>`).

- **From a canon session, edit files in a product repo but never commit, push or open pull requests there.** That is the product owner's call, made from a session in that repo.
- **The same rule holds in the other direction.** A product session may draft a canon file, but the commit happens from a session here.
- **An uncommitted edit in another repo can quietly disappear**: stashed with unrelated work, overwritten, reset. When a canon pass writes into a product repo, say so in the log entry, and check on the next pass that it actually landed. A log entry saying content was written is evidence of intent, not of landing.

## Facts and findings

- **Re-verify a finding against the repo before restating it.** A wrong observation copied from page to page gains authority with every copy. If it turns out wrong, correct it where it was recorded, visibly, instead of dropping it.
- **Check a pass against the repo, not against its own summary.** Grep for the specific claim.
- When a product page here says what a product does, it was true on the date written next to it. Re-check before relying on it.

## Writing

- Anything written for people outside the organization follows `00-canon/04-tone-of-voice.md` and `00-canon/07-writing-style-guide.md`. Terms come from `00-canon/05-terminology.md`.
- Absolute dates (YYYY-MM-DD), never "yesterday" or "next week".
- Say who raised something and when: "Raised by <name>, YYYY-MM-DD."
- Say what isn't decided yet. Every open thread ends with a **Not decided:** line; keep it current.

## Confidentiality

<If this repo is private: say what it holds and where its content may not go without asking first. Example: "This repo is private and holds unfinished business discussions. Don't copy its content into public repos or public pages without asking first.">

---

# Bootstrap Protocol

**Trigger:** the operator types `Bootstrap the canon`.

This section is the one-time setup. Its last step deletes it; the starter pack keeps the original.

To bootstrap a single file again, paste its BOOTSTRAP block back at the top of the file and run steps 1 to 6 below for that file only.

Before starting a full bootstrap, ask one question: **do product repos already exist?**

- **No, or only one:** run the interview below.
- **Yes, two or more:** run `04-process/extracting-a-canon.md` instead. It reads the existing repos first, so the interview starts from what the products already say rather than from a blank page.

Walk through the files in this order. For each file:

1. Read the file's BOOTSTRAP block for the shape the content should take.
2. Ask whether existing material exists (a deck, a website, a product repo's own docs). Offer to read it.
3. Otherwise, run the interview prompts in the block.
4. **Never invent content.** If the operator can't answer a section, mark it `TODO` and move on.
5. Show the proposed content and wait for confirmation before writing.
6. On confirmation, **replace the whole file** with the confirmed content: no BOOTSTRAP block, no "Run `Bootstrap`" status line, no sample rows left.

**Order:**

1. `00-canon/01-values-and-vision.md`
2. `00-canon/02-design-system.md`
3. `00-canon/03-ux-principles.md`
4. `00-canon/04-tone-of-voice.md`
5. `00-canon/05-terminology.md`
6. `00-canon/06-naming-conventions.md`
7. `00-canon/07-writing-style-guide.md`
8. `00-canon/08-development-workflow.md`: pre-filled. Walk the operator through it and ask only which steps to drop or add.
9. `00-canon/09-release-workflow.md`: pre-filled. Ask whether any product has a staged deployment; if none does yet, leave it as is.
10. `02-roadmap/portfolio-roadmap.md`: priorities and one Snapshot row per product.
11. **Finally:** fill in this file's placeholders (people, labels, branch, confidentiality) and `README.md`'s status section, delete the status line at the top, and delete this Bootstrap Protocol section.

Then tell the operator how to connect each product: `Bootstrap the project` in the product repo. It finds this canon and drafts the product's own rows here (its `01-products/<product>.md` page, its row in the per-product table of `01-values-and-vision.md`, its tokens row in `02-design-system.md`, its Snapshot row in the roadmap). Those drafts are committed from a session in this repo. Leave those per-product rows empty during this bootstrap, and keep any rows a project bootstrap already drafted: when a file here is replaced whole, its existing per-product rows carry over.

---

# Canon Review Protocol

**Trigger:** the operator types `Review the canon`.

Canon drifts in two directions: products drift away from canon, and canon's own pages about products go stale. Run both checks.

1. **Products against canon.** For each product repo: does its `CLAUDE.md` still carry the `Canon Alignment` block? Has a restatement of values, design principles or workflow crept back in? Grep for phrases from `00-canon/01-values-and-vision.md`.
2. **Canon against products.** For each `01-products/<product>.md` and its Snapshot row in the roadmap: re-read the product repo (git log, tags, plan, backlog) and correct what's no longer true. Date every row you re-check.
3. **Edits that should have landed.** For every log entry that says a canon pass wrote into a product repo: is it there?
4. **Open threads.** Is every **Not decided:** line still accurate? Is any `decision` issue settled in practice but not written down?

Report findings grouped as **Drift / Stale / Not landed / Undecided**, each with file and line. Propose edits; apply them only after approval. Log the review in the roadmap's Log section with the date.

A review older than 30 days is worth a one-line reminder at session start. Don't block work on it.
