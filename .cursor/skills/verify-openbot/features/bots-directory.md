# Bots directory and creating a Bot

Lists Bots by Needs you, Pinned, Yours, Shared with you and Hidden; creates a Bot, choosing where it runs and optionally registering an external AG-UI agent.

Area: Bots. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/bots`, `/team-bots`

## Sub-features

- `groups` (`Needs you`, `Pinned`, `Yours`, `Shared with you`, `Hidden`).
- `create-bot` (`Create a Bot`, `Where will your Bot run?`).
- `external-agent` registers an AG-UI endpoint (docs/coworkers.md).
- `hide-delete` hide or delete a Bot.
- `legacy` `/team-bots` redirects here.

## How to get to it (user POV)

- Sidebar Bots, or `/bots`.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **List.** `page.goto('/bots')`; headings `Yours`, `Shared with you`.
- **Create.** `getByRole('button', { name: 'Create a Bot' })`; answer `Where will your Bot run?`; save.
- **Proof.** Screenshot of the new card; `GET /api/agents` lists it.

## Gotchas

- Creating a Bot writes to Postgres; only on a local throwaway volume.
- Hidden Bots still exist; deletion is separate.
