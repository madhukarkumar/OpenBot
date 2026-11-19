# Goals (responsibilities)

Standing goals a Bot is responsible for; the Bot works toward them proactively.

Area: Bots. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/bots/$agentId/responsibilities`, `/responsibilities`

## Sub-features

- `add-goal`, `edit-goal`, `remove-goal`.
- `legacy` `/responsibilities` redirects.

## How to get to it (user POV)

- Bot page → Goals.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Open.** `page.goto('/bots/<id>/responsibilities')`; add a goal and save.
- **Proof.** Screenshot of the list.

## Gotchas

- Goals drive proactive runs that spend model tokens.
