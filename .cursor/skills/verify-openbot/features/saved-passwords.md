# Saved logins

Logins a person saves so Bots can sign in to websites without seeing the secret (used by sign-in requests).

Area: Settings. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/settings/passwords`

## Sub-features

- `saved-logins` (`Saved logins`).
- `add-remove` add or remove a login.

## How to get to it (user POV)

- Settings → Passwords.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Open.** `page.goto('/settings/passwords')`; `Saved logins`.
- **Proof.** Screenshot of the empty list only.

## Gotchas

- Never add a real password from an agent.
