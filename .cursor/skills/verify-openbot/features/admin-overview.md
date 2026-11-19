# Admin home and status

The administrator landing page linking every admin surface, with deployment status and the tenant package (agents, brand, model, skills, knowledge YAML).

Area: Admin. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/admin`, `/api/admin/status`, `/api/admin/package`

## Sub-features

- `status` deployment status.
- `tenant-package` YAML package view (`examples/fintech/` is a sample).

## How to get to it (user POV)

- Sidebar Admin (administrators only).

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Open.** `page.goto('/admin')`.
- **API.** `GET /api/admin/status`.
- **Proof.** Screenshot.

## Gotchas

- Members get a not-allowed page; single-user mode is always admin.
