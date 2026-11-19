# Approvals (personal, per-Bot and team)

Before a Bot acts it can be made to ask. People set their own rules and rules per Bot; administrators set team rules and handle shared-account requests. Pending approvals show in Needs you, on mobile, and in Slack/Teams cards.

Area: Approvals and governance. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/settings/approvals`, `/bots/$agentId/approvals`, `/admin/approvals`, `/approvals`

## Sub-features

- `personal` (`Ask before making changes`, `Rules for every Bot`, `Rules for other Bots`).
- `per-bot` (`Approval rules`, `Save rule`, `Add a rule`).
- `computer-commands` (`Commands on your computer`).
- `team` (`Team settings`, `Team rules`, `Add a team rule`, `Commands on members' computers, at most`).
- `shared-account-requests` (`Shared account requests`).
- `waiting` (`Waiting for your approval`, `Needs you`).
- `legacy` `/approvals` redirects.

## How to get to it (user POV)

- Settings → Approvals.
- Bot page → Approvals.
- Admin → Approvals.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Personal.** `page.goto('/settings/approvals')`; `Ask before making changes`.
- **Per Bot.** `page.goto('/bots/<id>/approvals')`; `Add a rule` → `Save rule`.
- **Team.** `page.goto('/admin/approvals')`; `Team rules`.
- **Proof.** Screenshots, then trigger a guarded action and screenshot `Waiting for your approval`.

## Gotchas

- Team rules cap personal ones; a personal rule cannot loosen a team rule.
- Saving a rule writes to Postgres; local volume only.
