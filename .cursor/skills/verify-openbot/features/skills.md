# Skills (personal and workspace)

Instructions Bots load on demand. People write their own (also from a conversation with the skill creator); workspace skills come from the tenant package and admins.

Area: Capabilities. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/capabilities/skills`, `/skills`, `/admin/skills`

## Sub-features

- `new-skill` (`New skill`).
- `edit-skill` (`Edit skill`).
- `workspace-skills` (`Workspace skills`).
- `skill-in-conversation` writing a skill from chat.
- `admin-installed` (`/admin/skills`, `Installed`).

## How to get to it (user POV)

- Capabilities → Skills.
- Admin → Skills.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Open.** `page.goto('/capabilities/skills')`; `New skill`.
- **Admin.** `page.goto('/admin/skills')`; `Installed`.
- **Proof.** Screenshots.

## Gotchas

- `/skills` and `/capabilities` redirect; link to the new paths.
