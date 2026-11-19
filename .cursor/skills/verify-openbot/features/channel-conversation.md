# Channel conversation with a Bot

A one-to-one channel with a coworker: send messages and files, get answers as components rather than prose, invoke skills with `/`, stop a run, and see what the Bot needs from you.

Area: Conversations. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/channel/new`, `/channel/$channelId`, `/api/channels`

## Sub-features

- `compose` (`Message`, `Attach a file`, `Stop the Bot`).
- `to-field` picks Bots; two or more Bots start a group.
- `components-in-chat` renders granted components in the transcript.
- `slash-skills` invokes a skill with `/`.
- `needs-you` shows questions and approvals waiting (`Needs you`, `Your answer`).
- `what-it-does` panel about the Bot (`This conversation's Bot`, `What it does`).

## How to get to it (user POV)

- `/channel/new` or a channel in the sidebar.
- Bots page → a Bot → start a channel.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.
- A model key in `.env` (spends money); use a cheap test prompt.

- **Start.** `page.goto('/channel/new')`; pick a Bot; type in `getByRole('textbox', { name: 'Message' })`; press Enter. URL becomes `/channel/<id>`.
- **Stop.** While it runs, `getByRole('button', { name: 'Stop the Bot' })` (testid `composer-stop`).
- **Needs you.** When the Bot asks, the `Needs you` region shows `Your answer`.
- **Proof.** Transcript screenshot plus the matching rows in `/admin/audit`.

## Gotchas

- Every turn calls the model and Intelligence; not runnable without paid keys.
- `transcript-stopped` and `bot-chat-history-unavailable` testids mark degraded states.
