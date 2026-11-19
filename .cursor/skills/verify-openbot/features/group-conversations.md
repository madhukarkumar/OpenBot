# Group conversations

Two or more Bots (and people, invited by email) in one channel; Bots can hand work to each other.

Area: Conversations. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/group/$channelId`, `/api/groups`

## Sub-features

- `start-group` puts two or more Bots in To:.
- `invite-person` (`Their email`, `Add`).
- `bot-handoff` one Bot asks another (see architecture: One Bot handing work to another).

## How to get to it (user POV)

- `/channel/new` with two Bots in To:.
- Legacy `/group/new` redirects to the new-conversation page.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.
- Two Bots configured.

- **Start.** In `/channel/new` add two Bots, send; URL becomes `/group/<id>`.
- **Invite.** `getByLabel('Their email')`, `Add`.
- **Proof.** Transcript showing both Bots.

## Gotchas

- Inviting a real email sends nothing locally only if delivery is unconfigured; use example.com addresses.
