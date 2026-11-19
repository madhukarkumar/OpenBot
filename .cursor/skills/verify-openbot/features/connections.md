# Connections (apps a person connects)

Each person connects the apps an administrator enabled (MCP servers, Composio apps, Arcade tools, Google Drive, Notion, Gmail) and sees each connection's tools and actions.

Area: Capabilities. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/connections`, `/connections/$key`, `/settings/connected-accounts`, `/settings/connected-accounts/$key`

## Sub-features

- `search` (`Search connections`).
- `connect` (`Connect`, `Continue to consent`).
- `disconnect` (`Disconnect`).
- `tools-actions` (`Tools`, `Actions`).
- `connected-accounts` settings view of the same.

## How to get to it (user POV)

- Sidebar Connections, or Settings → Connected accounts.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.
- At least one plugin enabled by an admin; real vendor accounts to connect.

- **List.** `page.goto('/connections')`; `getByLabel('Search connections')`.
- **Detail.** `page.goto('/connections/<key>')`; `Tools`.
- **Proof.** Screenshots; stop before `Continue to consent`.

## Gotchas

- Connecting goes to a real vendor's consent screen; never complete it unattended.
- Disconnecting a key does not revoke it at the vendor (docs/plugins/composio.md).
