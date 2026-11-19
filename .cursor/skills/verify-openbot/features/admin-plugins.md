# Plugins (MCP, Composio, Arcade)

Administrators register MCP servers and brokers (Composio, Arcade), enable apps, and grant tools per Bot; shared accounts let one connection serve a team.

Area: Admin. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/admin/plugins`, `/admin/plugins/$key`, `/admin/plugins/$key/bots/$agentId`, `/admin/plugins/$key/tools/$tool`, `/admin/plugins/composio`, `/admin/plugins/arcade`

## Sub-features

- `directory` (`Explore plugins`, plugin directory).
- `plugin-detail` per plugin.
- `grant-per-bot` tools granted to one Bot.
- `tool-detail` one tool's exposure.
- `composio` broker key and app catalogue.
- `arcade` Arcade tools and user verification.
- `shared-accounts` team-shared connections.

## How to get to it (user POV)

- Admin → Plugins.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.
- Broker keys (Composio, Arcade) for those pages to list apps.

- **Open.** `page.goto('/admin/plugins')`; `Explore plugins`.
- **Composio.** `page.goto('/admin/plugins/composio')`.
- **Proof.** Screenshots; do not enable apps on a shared deployment.

## Gotchas

- Composio enumerates hundreds of apps; 56 are deliberately not offered (docs/plugins/composio.md).
