# Signing a Bot in to a website

When a Bot hits a login wall it sends a private sign-in request; the person opens it and signs in by hand, uses a saved login, or enters a verification code. The Bot never sees the secret.

Area: Bot computer. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/sign-in/$requestId`, `/settings/passwords`

## Sub-features

- `sign-in-request` private page `/sign-in/<requestId>`.
- `by-hand` (`Sign in by hand`).
- `saved-login` (`Use a saved login`, `Enter your login`).
- `verification-code` (`Enter the verification code`).

## How to get to it (user POV)

- Link in `Needs you` or a notification.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.
- A Bot blocked on a login page so a request exists.

- **Open.** `page.goto('/sign-in/<requestId>')`; options `Sign in by hand`, `Use a saved login`.
- **Proof.** Screenshot only; do not complete a real sign-in.

## Gotchas

- Request ids are single-use and per person; an unknown id shows an error page.
- Never submit real credentials from an agent.
