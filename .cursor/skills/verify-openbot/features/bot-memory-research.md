# Bot memory and background research

What a Bot remembers and which app sources it learns from, plus background research it does on its own.

Area: Bots. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/bots/$agentId/memory`

## Sub-features

- `app-sources` (`App sources`).
- `background-research` (`Turn on background research`).
- `memories-list` view and remove memories.

## How to get to it (user POV)

- Bot page → Memory.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Open.** `page.goto('/bots/<id>/memory')`; `App sources`.
- **Proof.** Screenshot.

## Gotchas

- Background research runs in the background and spends tokens; public-web research needs a Parallel, Exa or Firecrawl key.
