# Onboarding

A first-time person is held on `/onboarding` until they finish it: it explains that each Bot has its own computer, lets them pick a Bot or make one, and shows the self-host message.

Area: Access and onboarding. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/onboarding`, `/api/me/onboarding`

## Sub-features

- `onboarding-gate` redirects every authed page to `/onboarding` until done.
- `pick-a-bot` (`Pick a Bot or make your own`).
- `first-message` uses the composer (`Message`).
- `self-host-banner` (`Self-host OpenBot`, `Dismiss`).

## How to get to it (user POV)

- First visit after sign-in.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.
- A fresh database (new volume) so onboarding has not been completed.

- **Open.** `page.goto('/')` redirects to `/onboarding`; text `Each Bot has its own computer`.
- **Pick.** Choose a Bot under `Pick a Bot or make your own`; the composer `getByRole('textbox', { name: 'Message' })` is ready.
- **Finish.** After completing, `page.goto('/bots')` no longer redirects.
- **Proof.** Screenshots before and after, plus `POST /api/me/onboarding` 200 in the network log.

## Gotchas

- Onboarding state is per user; reuse of a volume skips it.
- Sending a message spends model tokens.
