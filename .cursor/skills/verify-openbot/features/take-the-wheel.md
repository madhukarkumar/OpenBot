# Take control and hand back

A person can take control of the Bot's computer (for a login, captcha or a fiddly step) and hand it back; the Bot can also ask for help.

Area: Bot computer. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/channel/$channelId`, `/bot`

## Sub-features

- `take-control` (`Take control`).
- `hand-back` (`Hand back`).
- `help-request` the Bot asks a person via `Needs you`.
- `never-shown` fields marked `Never shown to the Bot`.

## How to get to it (user POV)

- Screen panel during a run.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.
- A Bot mid-task with its screen open.

- **Take.** `getByRole('button', { name: 'Take control' })`; the screen accepts input.
- **Return.** `getByRole('button', { name: 'Hand back' })`.
- **Proof.** Screenshots and the audit row for the control change.

## Gotchas

- Do not type real credentials during automated runs.
