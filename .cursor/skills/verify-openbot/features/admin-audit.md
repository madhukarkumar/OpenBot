# Audit log

Every governed action, approval and admin change, with filters and CSV export; retention is configurable.

Area: Approvals and governance. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/admin/audit`, `/api/admin/audit-events`

## Sub-features

- `filter` by actor, Bot, action.
- `export` (`Export CSV`).
- `otlp-export` (`Exporting over OTLP/HTTP.`) when configured.
- `retention` (`server/src/audit-retention.ts`).

## How to get to it (user POV)

- Admin → Audit.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Open.** `page.goto('/admin/audit')`; rows render.
- **API.** `GET http://localhost:3001/api/admin/audit-events` with the session cookie returns JSON.
- **Proof.** Screenshot and the JSON count.

## Gotchas

- Exports can contain conversation snippets; keep them out of repos.
