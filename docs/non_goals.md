<!-- BOOTSTRAP INSTRUCTIONS FOR CLAUDE CODE — fill me in via interview

## Goal of this file
Capture what this project will NOT do. Non-goals are as important as goals.
Without explicit non-goals, scope creep is silent — every well-meaning idea
looks reasonable and gets onto the plan. With this file, "no" has a written
reason.

## Interview prompts

1. "Do you have a written non-goals or 'out of scope' document already?
   Paste it. Otherwise we'll build one."

2. If starting fresh:

   a) "Name three things competitors do that you will explicitly NOT do.
      Be specific. 'We don't take custody'. 'We don't make predictions'.
      'We don't sell user data'."

   b) "For each: write one sentence explaining WHY. The why is what makes
      this a principle rather than a feature gap."

   c) "Is there a previous version, prototype, or PoC whose behavior should
      NOT carry over? List it. Mark it as 'imported as historical only'
      or 'explicitly not reproduced'."

   d) "Are there features customers will ask for that you'll always say
      no to? Anticipate them — the answer is easier to write before the
      pressure arrives."

3. "What does 'done' for V1 NOT include? Be honest. Multi-tenant? Mobile?
   Localization? List what V1 doesn't ship and accept it."

## What the final file should look like

Replace this BOOTSTRAP block. Suggested structure:

```
# Non-Goals & Compatibility Boundaries

**Status:** Frozen
**Default rule:** If a behavior is not explicitly listed as a v1 goal elsewhere,
it is a non-goal by default.

## 1. What this project will NOT do

### 1.1 <Non-goal>
- <one-paragraph explanation including the WHY>
- <if relevant: what this rules out specifically>

(repeat)

## 2. Compatibility boundaries with prior versions

(if applicable: what carries over and what doesn't)

## 3. What V1 explicitly does not ship

(features you've decided to defer, with the date you decided)
```

## Rules

- A non-goal without a WHY is just a feature gap. Always include the reason.
- Date your decisions to defer. Future-you needs to know when "later" became
  a real promise vs a vague intention.
- The non-goals file should grow over time, not shrink. Every time you say
  no to something significant, capture it here.

## Example — how Aurono Labs answered this

> **Default rule:** If a behavior is not explicitly listed as a v1 goal
> elsewhere, it is a non-goal by default.
>
> ### 3.1 PoC Decision Logic
> Aurono Start will **not**:
> - reuse PoC buy/sell evaluation code
> - preserve PoC evaluation order quirks
> - preserve BUY-before-SELL mutual exclusion rules
> - preserve PoC candle-close heuristics
>
> **Why:** PoC behavior is not a reference implementation. Aurono Start is a
> deliberate architectural reset — event-sourced, deterministic, auditable.
>
> ### 3.2 Custody
> Aurono will never hold user funds, even temporarily. Exchanges hold the
> money; Aurono only places orders via API.
>
> **Why:** Custody changes the trust model, the regulatory exposure, and the
> failure surface. Non-custody is a load-bearing wall of the product.

Source: Aurono Labs · auronolabs.com · `docs/v1_non_goals.md`.

END BOOTSTRAP -->

# Non-Goals & Compatibility Boundaries

> Run `Bootstrap the foundation` to fill in.

**Status:** Draft (pre-bootstrap)
**Default rule:** If a behavior is not explicitly listed as a v1 goal elsewhere, it is a non-goal by default.

<!-- Non-goals sections go here -->
