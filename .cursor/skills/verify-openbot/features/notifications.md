# Notifications and devices

Devices that get push notifications (desktop and mobile) and recent deliveries.

Area: Settings. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/settings/notifications`

## Sub-features

- `devices` (`Your devices`).
- `recent-deliveries` (`Recent deliveries`).

## How to get to it (user POV)

- Settings → Notifications.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Open.** `page.goto('/settings/notifications')`; `Your devices`.
- **Proof.** Screenshot.

## Gotchas

- Push needs a registered device (mobile app or desktop).
