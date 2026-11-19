# Routines

Standing instructions a Bot runs on a schedule. The routines worker (a CronJob in Kubernetes, `bun worker/src/index.ts` locally) fires them.

Area: Bots. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/routines`, `/bots/$agentId/routines`, `worker/`

## Sub-features

- `create-routine` from a conversation or the routines page.
- `schedule` 15-minute floor, 20-enabled cap per person.
- `pause-resume` (`Paused`, `Turn off`).
- `fatigue-rule` stops routines nobody reads.
- `missed-windows` skipped, not replayed.
- `runs-as` runs as the person who made it.

## How to get to it (user POV)

- Sidebar Routines (`/routines`).
- Bot page → Routines.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.
- The worker running (start.sh starts it).

- **List.** `page.goto('/routines')`.
- **Create.** Ask a Bot in chat to do something every morning, then confirm it appears.
- **Proof.** Screenshot and the worker log line for the next fire.

## Gotchas

- Without the worker nothing fires.
- Each fire spends model tokens; turn test routines off.
