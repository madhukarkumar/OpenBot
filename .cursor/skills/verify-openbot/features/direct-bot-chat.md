# Direct Bot chat

Chat with one Bot directly beside its computer; `?agent=<id>` selects which.

Area: Conversations. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/bot`, `/agents`

## Sub-features

- `select-agent` via `?agent=`.
- `computer-sidebar` (`Computer sidebar`, `Computer`).
- `legacy-agents` `/agents` redirects here.

## How to get to it (user POV)

- `/bot`
- README Try it: ask `Open news.ycombinator.com and tell me the top story.`

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.
- A model key.

- **Open.** `page.goto('/bot?agent=general-assistant')`; region `Computer sidebar`.
- **Ask.** Send the README prompt; the screen shows the browser navigating.
- **Proof.** Screenshot of transcript and screen.

## Gotchas

- Bot ids come from `examples/fintech/agents.yaml` and `agents/`; check the list on `/bots`.
