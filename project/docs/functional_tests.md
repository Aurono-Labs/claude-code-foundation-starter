<!-- BOOTSTRAP INSTRUCTIONS FOR CLAUDE CODE: fill me in via interview

## Goal of this file
Track manual / exploratory tests for each feature. Unlike automated tests,
these capture *user-observable* behavior that can't always be asserted in
code: "the dashboard renders in this order", "the empty state shows this
copy", "hovering this dot shows this tooltip".

Status of each test:
- **open**: defined, not yet executed
- **passed**: executed successfully
- **failed**: issue found (linked to fix or note)

## When to write tests here

In Phase 4 (Execution), after writing code but before committing, append
a block of functional test entries for the feature. Mark them all as `open`.
The operator runs them manually and updates statuses.

## Bootstrap action

For a brand-new project, this file just needs the header and a "how to use"
section. No content yet; content arrives in Phase 4 of the first feature.

Replace this BOOTSTRAP block with the structure below.

## What the final file should look like

```
# Functional Tests

This document tracks functional (manual / exploratory) tests performed after
feature execution.

- **open**: test defined, not yet executed
- **passed**: test executed successfully
- **failed**: test executed, issue found (link to fix or note)

## How to use this file

After each feature is built (Phase 4, Execution), Claude appends new test
entries with status `open`. The operator performs the tests and updates the
status to `passed` or `failed`. When all tests for a feature are closed, the
operator triggers Phase 6 (Closing).

## Tests

<!-- New functional test entries are appended below this line -->

### Phase X.Y: <Feature name>

**Date:** YYYY-MM-DD

<short description of what changed>

#### <Section grouping>
- [ ] **open**: <specific testable statement>
- [ ] **open**: <specific testable statement>
```

## Rules

- One bullet = one testable statement. Compound tests are forbidden; split
  them.
- Tests are written as imperative statements the operator can either confirm
  or refute in seconds.
- Group by visual / functional region of the feature (header, chart, drawer,
  empty state, error state).
- ALWAYS cover the four UI states for new pages/components that fetch data:
  loading, empty, error, populated.

END BOOTSTRAP -->

# Functional Tests

> Run `Bootstrap the project` to set up the structure.

<!-- Tests will be appended below this line during Phase 4 of each feature -->
