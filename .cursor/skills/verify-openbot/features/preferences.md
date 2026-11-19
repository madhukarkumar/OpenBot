# Preferences and standing instructions

Personal settings: dark theme, standing instructions every Bot follows, and keyboard shortcuts.

Area: Settings. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/settings`, `/api/settings/instructions`

## Sub-features

- `theme` (`Dark theme`).
- `standing-instructions` (`Standing instructions`).
- `shortcuts` (`Keyboard shortcuts`).

## How to get to it (user POV)

- Sidebar Settings.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Open.** `page.goto('/settings')`; toggle `Dark theme`.
- **API.** `GET /api/settings/instructions`.
- **Proof.** Screenshots light and dark.

## Gotchas

- Standing instructions go into every run's prompt.
