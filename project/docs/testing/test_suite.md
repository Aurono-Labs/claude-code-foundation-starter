<!-- BOOTSTRAP INSTRUCTIONS FOR CLAUDE CODE: fill me in via interview

## Goal of this file
Inventory the automated test suite: what frameworks are in use, where tests
live, and (most importantly) what each test file covers and why. This is
not test code; it's the *meta-documentation* of test code, so future
contributors don't have to grep to find what already exists.

## Interview prompts

1. "Is there an existing test setup? Frameworks, file conventions, CI?
   Share it."

2. If starting fresh:

   a) "What testing frameworks will the project use? Backend? Frontend?
      End-to-end?"

   b) "Where do tests live? File / directory convention?"

   c) "How do you run them? Fast suite vs full suite. CI vs local."

   d) "Are there testing rules? E.g. 'integration tests must hit a real
      database, not mocks', 'every UI component handles four states:
      loading, empty, error, populated'."

3. "Are there tests already written? List them, one row per file,
   columns: file, test count, what it covers."

## What the final file should look like

Replace this BOOTSTRAP block. Suggested structure:

```
# Test Suite

## Running Tests

    <fast suite command>
    <full suite command>
    <watch mode>

## Backend Tests

**Framework:** <framework>
**Location:** <path convention>

### <Module>
| File | Tests | What it covers |
|---|---|---|
| ... | ... | ... |

## Frontend Tests

**Framework:** <framework>
**Config:** <config file path>

| File | Tests | What it covers |
|---|---|---|

## End-to-End Tests (if applicable)

## Testing Rules

- <rule>: <reason>
- <rule>: <reason>
```

## Rules

- One row per test file. Drift between this document and reality is a sign
  the project is healthy enough to need a foundation review.
- Updated in Phase 4 (Execution) whenever new test files are added.
- The "What it covers" column is for *humans reading later*, not for the
  CI machine. Write it like you'd describe the file to a new colleague.

END BOOTSTRAP -->

# Test Suite

> Run `Bootstrap the project` to fill in.

<!-- Test inventory sections go here -->
