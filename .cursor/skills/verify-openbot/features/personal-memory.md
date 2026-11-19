# Personal memory

Facts a person asks Bots to remember about them, shared across their Bots; stored in CopilotKit Intelligence.

Area: Capabilities. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/capabilities/memory`, `/memory`, `/settings/memory`

## Sub-features

- `remember` (`Remember`).
- `list` (`Your memories`).
- `forget` remove a memory.
- `legacy` `/memory` and `/settings/memory` redirect.

## How to get to it (user POV)

- Capabilities → Memory.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Open.** `page.goto('/capabilities/memory')`; `Your memories`.
- **Proof.** Screenshot.

## Gotchas

- Memory lives in Intelligence, not Postgres; it needs the Intelligence key.
