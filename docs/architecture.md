<!-- BOOTSTRAP INSTRUCTIONS FOR CLAUDE CODE — fill me in via interview

## Goal of this file
Capture the technical architecture: stack, structure, key design decisions,
deployment model, and the architectural rules that must not be broken. New
contributors should be able to read this and understand both *what* the
system is and *why* it's that shape.

## Interview prompts

1. "Do you have existing architecture documentation, an ADR folder, or a
   whiteboard sketch you've photographed? Share it."

2. If starting fresh:

   a) "What is the runtime — server, edge, on-device, hybrid? Why this
      choice and not the others?"

   b) "What's the stack? Languages, frameworks, datastore, infra. Be
      specific."

   c) "What's the deployment topology? Single binary? Containerized?
      Multi-service? Where does it run — your servers, the user's
      device, both?"

   d) "What are the 3-5 architectural rules that, if broken, would
      compromise the project's core values? Examples: 'UI never
      contains business logic', 'events are append-only',
      'no synchronous calls between service A and B'."

3. "What did you explicitly choose NOT to use? Frameworks, patterns,
   architectures. The negative list is as informative as the positive."

4. "Are there architectural decisions you've made that future-you might
   want to revisit? Mark them with a date so the next review can revisit."

## What the final file should look like

Replace this BOOTSTRAP block. Suggested structure:

```
# Architecture

## Stack
| Layer | Technology | Reason |
|---|---|---|
| ... | ... | ... |

## Deployment
- Topology: <describe>
- Process model: <describe>
- Data location: <describe>

## Key Design Decisions
### <Decision name>
- **Choice:** ...
- **Alternatives considered:** ...
- **Reason:** ...
- **Date:** YYYY-MM-DD

## Architectural Rules (Non-Negotiable)
1. <Rule> — <reason>
2. ...

## What We Explicitly Do Not Use
- <Technology / pattern> — <reason>
```

## Rules

- Every key decision has a date. Architectures age; dates make age visible.
- Every rule has a reason. A rule without a reason becomes folklore.
- Update this file in Phase 4 of the workflow whenever architecture changes,
  not as a separate documentation pass.

## Example — how Aurono Labs answered this

> ### Deployment topology
> Aurono Start runs on a Raspberry Pi as a systemd service.
>
> | Component | Path |
> |---|---|
> | Application code | `/opt/aurono/` |
> | Python venv | `/opt/aurono/venv/` |
> | Built frontend | `/opt/aurono/frontend/dist/` |
> | Database | `/var/lib/aurono/aurono.db` |
> | Encryption keys | `/var/lib/aurono/keys/` |
> | Config (env vars) | `/etc/aurono/aurono.env` |
>
> ### Key design decisions
> - **Single process** — FastAPI serves both API and built frontend SPA.
>   No nginx, no reverse proxy.
> - **Dedicated system user** `aurono` — no shell, restricted to
>   `/opt/aurono` and `/var/lib/aurono`.
> - **systemd hardening** — `ProtectHome=true`, `ProtectSystem=strict`,
>   `NoNewPrivileges=true`.
> - **Supply chain hardening** — `requirements.lock` with SHA256 hashes
>   (`pip install --require-hashes`), `npm ci` for strict lockfile installs.
>
> ### Architectural rules (non-negotiable)
> 1. **UI must never become logic.** The frontend can reorder blocks and
>    visually connect nodes, but the backend must validate, compile, persist,
>    and emit deterministic events. UI = representation only.
> 2. **Events are append-only.** Never edited, never deleted.

Source: Aurono Labs · auronolabs.com · `docs/Aurono_Start_V1_architecture.md`.

END BOOTSTRAP -->

# Architecture

> Run `Bootstrap the foundation` to fill in.

<!-- Architecture sections go here -->
