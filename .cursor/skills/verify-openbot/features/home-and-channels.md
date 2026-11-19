# Home, channel list and search

The home screen starts a conversation and lists channels with unread markers; the sidebar holds New conversation, search and the Bots.

Area: Conversations. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/`, `/channel/new`

## Sub-features

- `start-conversation` (`Start a conversation`, composer `Message`).
- `explore-bots` (`Explore Bots`).
- `new-conversation` (`New conversation`).
- `search` (`Search conversations`).
- `unread` (`Unread messages`).
- `attach` (`Attach a file`).

## How to get to it (user POV)

- `/` after sign-in.
- Sidebar `New conversation`.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Home.** `page.goto('/')`; `getByText('Start a conversation')` and `getByRole('textbox', { name: 'Message' })`.
- **New.** `getByRole('button', { name: 'New conversation' })` opens `/channel/new`.
- **Search.** `getByRole('searchbox', { name: 'Search conversations' })` (or `getByLabel('Search conversations')`) filters the list.
- **Proof.** ARIA snapshot of the sidebar.

## Gotchas

- Threads are stored in CopilotKit Intelligence; without its key the server refuses to start.
- Accessible names come from props; confirm with an ARIA snapshot before hard-coding roles.
