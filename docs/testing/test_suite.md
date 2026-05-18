<!-- BOOTSTRAP INSTRUCTIONS FOR CLAUDE CODE — fill me in via interview

## Goal of this file
Inventory the automated test suite: what frameworks are in use, where tests
live, and — most importantly — what each test file covers and why. This is
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

3. "Are there tests already written? List them — one row per file,
   columns: file, test count, what it covers."

## What the final file should look like

Replace this BOOTSTRAP block. Suggested structure:

```
# Test Suite

## Running Tests

```bash
<fast suite command>
<full suite command>
<watch mode>
```

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

- <rule> — <reason>
- <rule> — <reason>
```

## Rules

- One row per test file. Drift between this document and reality is a sign
  the project is healthy enough to need a foundation review.
- Updated in Phase 4 (Execution) whenever new test files are added.
- The "What it covers" column is for *humans reading later*, not for the
  CI machine. Write it like you'd describe the file to a new colleague.

## Example — how Aurono Labs answered this

> ### Running tests
> ```bash
> # Frontend (cwd is frontend/)
> cd frontend && npm test           # single run
> cd frontend && npm run test:watch # watch mode
>
> # Backend
> python -m pytest                  # full suite (~5min)
> python -m pytest -m "not slow"    # fast suite (~7s, 353 tests)
> ```
>
> ### Backend: Analytics
> | File | Tests | What it covers |
> |---|---:|---|
> | `tests/analytics/test_milestones.py` | 18 | `_detect_first_trade`, `_detect_trade_count` (10/25/50 sells), `_detect_portfolio_peak` (dual condition: value + units, 7 edge cases incl. price drift, post-sell, deposit). |
> | `tests/analytics/test_benchmarks.py` | 14 | `net_injected_capital`, `compute_buy_and_hold_series`, `compute_dca_series` (monthly bucketing across calendar months), `compute_benchmark_comparison` (Phase 15.23). |
>
> ### Frontend: Vitest + jsdom
> | File | Tests | What it covers |
> |---|---:|---|
> | `src/lib/humanize.test.ts` | 58 | `statusLabel`, `timeframeToWords`, `friendlySymbol`, `eventToSentence` (14 event types), `relativeTime`, `dateGroupLabel`. |
> | `src/lib/__tests__/triggerAnalysis.test.ts` | 31 | `computeSigmaThresholds`, `runTriggerSimulation` (BUY/SELL executed/ignored, ACB protection, cooldown, fee tracking, benchmarks). |
>
> ### Testing rules
> - Integration tests hit a real database, not mocks.
> - `tsc -b` runs alongside vitest — vitest's esbuild ignores `noUnusedLocals`
>   etc.; the Pi install runs `tsc -b`, so both must pass before claiming green.
> - Every UI component handles four states: loading, empty, error, populated.

Source: Aurono Labs · auronolabs.com · `docs/testing/TEST-SUITE.md`.

END BOOTSTRAP -->

# Test Suite

> Run `Bootstrap the foundation` to fill in.

<!-- Test inventory sections go here -->
