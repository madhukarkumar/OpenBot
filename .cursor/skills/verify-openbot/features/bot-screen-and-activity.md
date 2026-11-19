# Watching a Bot's screen and activity

Each Bot works on its own computer (Chromium plus `/workspace`). The channel shows a live screen beside the transcript; the Bot page's Activity tab lists what it did.

Area: Bot computer. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/channel/$channelId`, `/bot`, `/bots/$agentId (Activity)`

## Sub-features

- `live-screen` (`The Bot's screen`, `Open the Bot's screen full size`, `Close the Bot's screen`).
- `computer-sidebar` (`Computer sidebar`).
- `activity-tab` (`Activity` on the Bot page).
- `working-files` files in `/workspace` shown beside the conversation.

## How to get to it (user POV)

- Any channel while a Bot uses its browser.
- `/bots/<id>` → `Activity`.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.
- Docker running so `agent-computer` (port 4100) and the supervisor (4500) are up; a model key.

- **Screen.** In a channel, ask the Bot to open a page; `getByRole('region', { name: "The Bot's screen" })` shows it.
- **Full size.** `getByRole('button', { name: "Open the Bot's screen full size" })`, then `Close the Bot's screen`.
- **Proof.** Two screenshots and the audit rows for the browser actions.

## Gotchas

- With `OPENBOT_ONE_COMPUTER_EACH=false` all Bots share one computer.
- Screens are pictures streamed from the computer container; nothing renders if Docker is down.
