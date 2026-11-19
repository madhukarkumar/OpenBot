# Automatic learning

Bots contribute conversations to a Learning container that proposes skills; an admin reviews and publishes them to Bots.

Area: Admin. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/admin/learning`

## Sub-features

- `automatic-learning` (`Automatic learning`).
- `review-publish` (`Review and publish`).
- `assignment` which Bots contribute and receive.

## How to get to it (user POV)

- Admin → Learning.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.
- A Learning container in CopilotKit Intelligence (docs/automatic-learning.md).

- **Open.** `page.goto('/admin/learning')`.
- **Proof.** Screenshot.

## Gotchas

- Managed vs self-hosted deployments differ (docs/automatic-learning.md).
