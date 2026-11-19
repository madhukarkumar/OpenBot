# Mobile app (Expo)

A phone companion: conversations, Bots, approvals, the Bot's computer, memory, plugins, routines and rules, with push notifications.

Area: Clients and platform. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `mobile/app/*`

## Sub-features

- `home` and `conversation`.
- `bots` and `bot`.
- `approvals` and `rules`.
- `computer` live screen.
- `memory`, `plugins`, `routine`.
- `push` (`mobile/src/notifications.ts`).

## How to get to it (user POV)

- Expo build (`mobile/eas.json`).

## Driving it with Playwright

Preconditions:

- Expo/EAS tooling and a reachable OpenBot URL.

- **Drive.** Not covered by Playwright; run with Expo against a local server.
- **Proof.** Simulator screenshots.

## Gotchas

- Uses its own `package-lock.json`, not the Bun workspace.
