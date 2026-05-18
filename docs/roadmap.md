<!-- BOOTSTRAP INSTRUCTIONS FOR CLAUDE CODE — fill me in via interview

## Goal of this file
Capture *what is being shipped, in what order*. The roadmap teaches Claude
Code the difference between "now", "later", and "never". It is the single
authority on phase boundaries. New ideas get triaged against the roadmap
before they enter the backlog.

## Interview prompts

1. "Do you have an existing roadmap — a Notion page, a slide, a public
   roadmap on a website? Share it and I'll synthesize. Otherwise we'll
   build it together."

2. If building from scratch:

   a) "What is the single thing you are shipping FIRST? Not the long-term
      vision — the first usable thing a real customer can get value from.
      Give it a name and a one-paragraph scope."

   b) "What is the date window? Quarter is fine — be honest, not ambitious."

   c) "What's the next phase after that — assuming Phase 1 ships? Same
      shape: name, scope, date window."

   d) "Repeat for as many phases as you can see clearly. Stop when you
      hit guesswork. It's better to have three real phases than seven
      pretend ones."

3. For each phase, ask:

   - "What capabilities does this phase add?"
   - "What is the scope boundary — what does it NOT include?"
   - "If applicable: what is open source and what is proprietary?"
   - "What's the ecosystem implication? Partnerships, integrations, revenue?"

4. End with: "Is there a long-term endgame for this product family that
   gives the phases their direction?"

## What the final file should look like

Replace this BOOTSTRAP block. Suggested structure per phase:

```
## Phase N — <Name>
**Timeline:** <quarter/year>
**Focus:** <one-line>

<one or two paragraphs describing the phase: what ships, why it's the next
step, what it explicitly does NOT cover. Reference the vision file where
relevant.>

**Open source scope:** <if applicable>
**Proprietary scope:** <if applicable>
```

End with a short **Summary** section connecting the phases to the vision.

## Rules

- Dates are honest, not optimistic. Better to be late on a date you wrote
  than miss a date you invented.
- Each phase has an explicit boundary. "What this phase does not include"
  is as important as what it does.
- The vision should be derivable from the sum of the phases. If it isn't,
  one of the two is wrong.

## Example — how Aurono Labs answered this

> ## Phase 1 — Aurono Start
> **Timeline:** 2026 Q1
> **Focus:** Local, execution-only crypto trading
>
> Establishes the foundation of the platform. Production-ready, deterministic
> execution engine running locally on a hardened Raspberry Pi. Users define
> trading rules upfront; Aurono executes them exactly, no discretion or
> prediction. Auditable and reproducible — users can always understand *why*
> a trade occurred.
>
> **Open-source scope:** strategy evaluation engine, decision/event builders,
> settlement model, ledger and portfolio math, event schemas, reporting,
> analytics computation, exchange adapter interfaces, Lab analysis core.
> **Proprietary scope:** exchange adapters, Lab product UI, frontend
> application, deployment tooling.
>
> ## Phase 2 — Aurono Portfolio (2026 Q2)
> Portfolio-aware execution and visibility across multiple exchanges.
>
> ## Phase 3 — Aurono Strategy Store (2026 Q4)
> Strategy choice without surrendering control. Mandatory rule transparency.
>
> ## Phase 4 — Aurono Multi-Asset (2027)
> Local, transparent capital portfolio manager beyond crypto.
>
> ## Phase 5 — Aurono Infrastructure (parallel)
> Execution layer embeddable into partner products. Aurono Foundation
> formalizes stewardship of the open core.

Source: Aurono Labs · auronolabs.com · `docs/Aurono_Roadmap.md`.

END BOOTSTRAP -->

# Product Roadmap

> Run `Bootstrap the foundation` to fill in.

<!-- Per-phase entries go here -->

## Summary

<!-- short paragraph connecting phases to vision -->
