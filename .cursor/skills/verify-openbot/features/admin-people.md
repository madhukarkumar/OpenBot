# People and roles

Who is in the deployment, their role (admin or member) and access.

Area: Admin. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/admin/people`, `/api/admin/people`, `/api/admin/people/:userId/role`, `/api/admin/people/:userId/access`

## Sub-features

- `search` (`Search people`).
- `who-is-here` (`Who is here`).
- `role` change role.
- `access` grant or remove access.

## How to get to it (user POV)

- Admin → People.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Open.** `page.goto('/admin/people')`; `Search people`.
- **Proof.** Screenshot.

## Gotchas

- Role changes are audited and take effect immediately.
