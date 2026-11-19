# A Bot's page

One Bot's home: what it can do for you, what needs you, background research and activity, with links to its settings tabs.

Area: Bots. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/bots/$agentId`

## Sub-features

- `for-you` (`For you`).
- `needs-you` (`Needs you`).
- `background-research` (`Background research`).
- `activity` (`Activity`).
- `settings-tabs` (`Settings for this Bot`): Goals, Routines, Reach, Memory, Approvals, Access, Setup, Sharing.

## How to get to it (user POV)

- `/bots` → a Bot card.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Open.** `page.goto('/bots/general-assistant')`; navigation `Settings for this Bot`.
- **Proof.** ARIA snapshot of the tabs.

## Gotchas

- Bot ids depend on the tenant package; `general-assistant` is in `examples/fintech/agents.yaml`.
