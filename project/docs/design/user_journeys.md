<!-- BOOTSTRAP INSTRUCTIONS FOR CLAUDE CODE — fill me in via interview

## Goal of this file
Map who does what, when. Features should attach to journeys, not the other
way around. A feature that doesn't sit on a real journey is a feature
looking for a customer.

## Interview prompts

1. "Do you have existing user research, journey maps, persona docs?
   Share them."

2. If starting fresh:

   a) "Describe the *first session* of a brand-new user. They just
      installed / signed up. What's the first thing they see? The
      first thing they do? The first decision they make?"

   b) "Describe the *typical day* of an active user. What brings them
      back? Daily, weekly, monthly cadences?"

   c) "Describe a *failure path*. Something has gone wrong — for them
      or for the system. How do they find out? What's their next move?"

   d) "Describe a *churn moment*. When they would leave. What would
      catch it before they do?"

3. "Are there secondary users? Admins, observers, family members,
   integration partners? Capture their journeys separately."

## What the final file should look like

Replace this BOOTSTRAP block. Suggested structure:

```
# User Journeys

## Primary user: <name / archetype>

### Journey 1: First session
1. <step> → <what they see / feel>
2. <step> → ...
N. Outcome: <what they walk away with>

### Journey 2: Typical day
### Journey 3: Failure path
### Journey 4: Churn moment

## Secondary users (if applicable)
```

## Rules

- Each journey is numbered, ordered, specific. Not a flowchart — a sequence
  of human moments.
- Each step describes both the action AND the feeling / understanding.
- Features that aren't on a journey go in the parked list — not the plan.
- Updated in Phase 6 (Closing) whenever a feature introduces, extends, or
  changes a journey.

## Example — how Aurono Labs answered this

> ## Primary user: non-technical crypto holder
> Parent with a day job. Read about Bitcoin in the news, bought some on a
> regulated exchange, wants disciplined rule-based trading without becoming
> a trader. Gets anxious when they see red numbers — associates red with
> losing money.
>
> ### Journey 1: First session (out of the box)
> 1. Plugs in the device → boots in < 60s → captive WiFi portal greets them
>    → "Your device is ready. Pick your WiFi."
> 2. Opens the browser → reaches `aurono.local` → setup wizard begins
>    → feels: *guided, not interrogated.*
> 3. Enters exchange API keys via UI wizard (never an env file or terminal)
>    → wizard verifies connectivity → green check appears
>    → feels: *the system understands what's working.*
> 4. Lands on Dashboard with zero holdings → empty state copy:
>    *"No strategies yet — create your first one"* (not a blank canvas)
> 5. Opens Lab → Explore tab → sees regime-first asset hierarchy
>    (Bullish / Bearish / Ranging / Overbought / Oversold)
> 6. Picks a starter strategy → pre-filled defaults → accepts as-is
> 7. Strategy runs in shadow mode automatically → no live trades yet
>    → feels: *calm confidence — nothing risked, learning begun.*
>
> Outcome: device is working, no money at risk, the user has a working
> mental model of what Aurono will do.

Source: Aurono Start (reference implementation by Aurono Labs · auronolabs.com) · `docs/design/USER-JOURNEYS.md`.

END BOOTSTRAP -->

# User Journeys

> Run `Bootstrap the foundation` to fill in.

<!-- Journey sections go here -->
