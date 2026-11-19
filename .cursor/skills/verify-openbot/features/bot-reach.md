# Reach (Slack, Teams, SMS and other destinations)

Where a Bot can reach people outside the app: Slack and Microsoft Teams through the OpenTag pairing (`server/src/delivery/opentag.ts`), SMS through Twilio, and push to devices; plus connecting a conversation to a destination.

Area: Bots. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/bots/$agentId/reach`, `/reachability`

## Sub-features

- `connected-destinations` (`Connected destinations`).
- `connect-conversation` (`Connect a conversation`, `Choose a Bot`, `Choose a conversation`).
- `phone` (`Send verification code`, `Confirm phone`).
- `legacy` `/reachability` redirects.

## How to get to it (user POV)

- Bot page → Reach.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.
- An OpenTag deployment for Slack/Teams (`AGENT_URL`, shared `AGENT_AUTH_HEADER`) or Twilio credentials for SMS.

- **Open.** `page.goto('/bots/<id>/reach')`; region `Connected destinations`.
- **Proof.** Screenshot only; connecting needs real provider accounts.

## Gotchas

- `Send verification code` sends a real SMS; never trigger it unattended.
