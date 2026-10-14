# Proposing a Change to Canon

## The rule

Any change to what lives in `00-canon/` starts here, not in a product repo. A product repo can adapt canon on purpose, as long as the adaptation is logged with its reason in `01-products/<product>.md`. What a product repo can't do is quietly restate or reinterpret canon locally: that is how drift starts.

## How a canon change gets made

1. **Surface it.** Something is inconsistent, missing or needs deciding.
2. **Lay out the real options**, not one pre-decided answer. Cite evidence for each: existing usage, earlier reasoning, the audience it has to land with.
3. **The decision owner decides**, case by case. A canon change is never inferred from what most products happen to do.
4. **Write the decision into the canon file itself.** Not only into a log, an issue or a chat. Canon is only a source of truth if it's current.
5. **Propagate.** Follow `sync-checklist.md`. Each product picks up the change at its next canon check; the change is real from step 4, not from when the last repo catches up.

## What goes in a product page instead

A product that needs to differ on purpose: one line in its `01-products/<product>.md` adaptations table, with the reason. That's not a canon change.

## What needs neither

Bug fixes, feature work, anything that isn't shared foundational content. This process is for the small, slow layer, not a gate on product development.
