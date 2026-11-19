# Saved credentials (team)

Team credentials Bots can use without seeing them, encrypted at rest.

Area: Admin. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/admin/credentials`, `/api/admin/credentials`

## Sub-features

- `list` (`Saved credentials`).
- `add` (`Save credential`).

## How to get to it (user POV)

- Admin → Credentials.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Open.** `page.goto('/admin/credentials')`; `Saved credentials`.
- **Proof.** Screenshot of the list only.

## Gotchas

- Never save a real credential from an agent; never screenshot a revealed value.
