<!-- BOOTSTRAP INSTRUCTIONS FOR CLAUDE CODE — fill me in via interview

## Goal of this file
Track manual / exploratory tests for each feature. Unlike automated tests,
these capture *user-observable* behavior that can't always be asserted in
code: "the dashboard renders in this order", "the empty state shows this
copy", "hovering this dot shows this tooltip".

Status of each test:
- **open** — defined, not yet executed
- **passed** — executed successfully
- **failed** — issue found (linked to fix or note)

## When to write tests here

In Phase 4 (Execution), after writing code but before committing, append
a block of functional test entries for the feature. Mark them all as `open`.
The operator runs them manually and updates statuses.

## Bootstrap action

For a brand-new project, this file just needs the header and a "how to use"
section. No content yet — content arrives in Phase 4 of the first feature.

Replace this BOOTSTRAP block with the structure below.

## What the final file should look like

```
# Functional Tests

This document tracks functional (manual / exploratory) tests performed after
feature execution.

- **open** — test defined, not yet executed
- **passed** — test executed successfully
- **failed** — test executed, issue found (link to fix or note)

## How to use this file

After each feature is built (Phase 4 — Execution), Claude appends new test
entries with status `open`. The operator performs the tests and updates the
status to `passed` or `failed`. When all tests for a feature are closed, the
operator triggers Phase 6 — Closing.

## Tests

<!-- New functional test entries are appended below this line -->

### Phase X.Y — <Feature name>

**Date:** YYYY-MM-DD

<short description of what changed>

#### <Section grouping>
- [ ] **open** — <specific testable statement>
- [ ] **open** — <specific testable statement>
```

## Rules

- One bullet = one testable statement. Compound tests are forbidden — split
  them.
- Tests are written as imperative statements the operator can either confirm
  or refute in seconds.
- Group by visual / functional region of the feature (header, chart, drawer,
  empty state, error state).
- ALWAYS cover the four UI states for new pages/components that fetch data:
  loading, empty, error, populated.

## Example — how Aurono Labs answered this

> ### Phase 15.23 — Evaluate Tab: Rebuild around Simulate-style dual chart
> **Date:** 2026-04-05
>
> The Evaluate tab has been rebuilt from 9 sections to 4 elements: header +
> verdict line, key metrics strip, dual-panel chart, three insight cards,
> one audit drawer with tabs.
>
> #### Shape & layout
> - [ ] **passed** — Open `/strategies?mode=lab&lab=evaluate` and pick a
>       strategy with deposit history. Verify the page renders top-to-bottom:
>       header, verdict paragraph, Deposit/Withdraw buttons, dual-panel chart,
>       three insight cards in one row, single "Audit trail" collapsible.
> - [ ] **passed** — Verify the old "Trade history", "Performance deep dive",
>       and "Trigger calibration" sections no longer appear as top-level.
>
> #### Verdict sentence
> - [ ] **passed** — Verdict includes: days running, total P&L, benchmark
>       deltas (vs buy & hold and vs DCA), and trade count summary.
> - [ ] **open** — For a strategy with no deposits yet, verify the verdict
>       still renders without benchmark deltas (graceful degradation).
> - [ ] **passed** — For a strategy with zero trades, verdict ends with
>       "No trades yet." instead of a trade count.

(The real Aurono Functional_Tests.md is ~1,600 lines. Every Phase 4
deliverable adds a block like this; the pre-commit hook blocks user-facing
code commits that don't also touch this file.)

Source: Aurono Labs · auronolabs.com · `docs/Functional_Tests.md`.

END BOOTSTRAP -->

# Functional Tests

> Run `Bootstrap the foundation` to set up the structure.

<!-- Tests will be appended below this line during Phase 4 of each feature -->
