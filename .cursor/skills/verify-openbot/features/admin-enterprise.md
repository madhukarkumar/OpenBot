# Enterprise controls

Deployment-wide switches: require SSO, only approved MCP servers, a model allowlist, and action recording.

Area: Admin. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/admin/enterprise`, `/api/admin/enterprise`

## Sub-features

- `require-sso` (`Require SSO`).
- `approved-mcp` (`Only approved MCP servers`).
- `model-allowlist` (`Model allowlist`).
- `action-recording` (`Action Recording`).

## How to get to it (user POV)

- Admin → Enterprise.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Open.** `page.goto('/admin/enterprise')`.
- **Proof.** Screenshot.

## Gotchas

- `Require SSO` can lock out single-user setups.
