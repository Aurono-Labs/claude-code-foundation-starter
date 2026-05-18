<!-- BOOTSTRAP INSTRUCTIONS FOR CLAUDE CODE — fill me in via interview

## Goal of this file
Lock the vocabulary of the project. Every term defined here is **write-once**:
it must never be renamed, overloaded, or reinterpreted across code, events,
documentation, or UI. If a new concept appears, introduce a new term — don't
reuse an old one.

The cost of this file is 20 minutes once. The payoff is years of avoided
ambiguity. The largest single cause of code rot is two people using the same
word for different things; this file kills that cause before it grows.

## Interview prompts

1. "Do you have a glossary or terminology document already? Paste it. If not,
   we'll generate the first version from the words you use most often."

2. If starting from scratch:

   a) "Name the 5–10 core nouns of your domain. Not the technical ones —
      the things real users would name. Examples in trading: 'trade',
      'order', 'fill'. Examples in healthcare: 'patient', 'visit',
      'prescription'."

   b) "For each noun: write the one-sentence definition you'd defend in
      front of a customer. Be precise."

   c) "What words are easy to confuse? E.g. 'order' and 'trade'? 'plan'
      and 'subscription'? List the confusable pairs and decide right now
      which means what."

   d) "Are there terms you used in an earlier project / prototype that
      MUST NOT carry over because they had different meaning then?
      Mark them as forbidden."

3. "What are the verb forms? In trading: 'decision' (verb-noun for
   logical conclusion) vs 'execution' (verb-noun for external action).
   These also need locking."

4. End with: "Do you want to declare any term as v1-locked vs v2-extensible?
   Some terms must never change; others may evolve."

## What the final file should look like

Replace this BOOTSTRAP block. Suggested structure:

```
# <Project> Domain Terminology — v1.0 (Locked, Canonical)

**Status:** Locked
**Version:** v1.0
**Rule:** Terms defined here are write-once. Synonyms are forbidden.

## 1. <Category — e.g. Capital, Decision Flow, Trading>

### 1.1 <Term>
**Definition:** > <one-sentence definition>
**Properties:** <bulleted properties>
**Used in:** <where this term appears — events, projections, UI labels>
**Explicitly NOT:** <what this term must never mean>

(repeat for each term)

## N. Forbidden Substitutions

- <term A> ≠ <term B>
- <term C> ≠ <term D>

## Final Rule

> If you feel the urge to reuse a term for a new meaning,
> you need a new term instead.
```

## Rules

- Every term has an "Explicitly NOT" entry. The negative space defines the
  term as much as the positive.
- No synonyms. If two words mean the same thing, pick one and outlaw the
  other.
- Forbidden substitutions are listed explicitly at the end so any contributor
  can scan them in 30 seconds.

## Example — how Aurono Labs answered this

> ### 2.1 Decision
> **Definition:** A decision is Aurono concluding that strategy conditions
> are met (or not).
> **Properties:** Purely logical · Deterministic · No side effects · Never
> changes capital or inventory.
> **Used in:** `BuyDecisionTriggered`, `SellDecisionTriggered`,
> `NoActionDecision`, `DecisionRejected`.
>
> ### 2.2 Intent
> **Definition:** An intent is Aurono committing to attempt an action.
> **Properties:** First irreversible step · Creates a durable `trade_id` ·
> May still fail or be cancelled.
> **Rule:** No exchange interaction may occur without an intent.
>
> ### Forbidden substitutions
> - allocation ≠ reservation
> - execution ≠ decision
> - order ≠ trade
> - intent ≠ decision
> - trade ≠ round trip
>
> ### Final rule
> "If you feel the urge to reuse a term for a new meaning, you need a new
> term instead." — v1.0, locked.

Source: Aurono Start (reference implementation by Aurono Labs · auronolabs.com) · `docs/domain_terminology.md`.

END BOOTSTRAP -->

# Domain Terminology — v1.0 (Locked, Canonical)

> Run `Bootstrap the foundation` to fill in.

**Status:** Draft (pre-bootstrap)
**Version:** v1.0
**Rule:** Terms defined here are write-once. Synonyms are forbidden.

<!-- Terminology sections go here -->

## Final Rule

> If you feel the urge to reuse a term for a new meaning, you need a new term instead.
