# Computers

Every computer in the deployment (Bot containers from the supervisor, and people's own computers via the desktop app): what each is doing, approved folders, egress, and controls to stop, reset, update or revoke.

Area: Admin. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/admin/computers`

## Sub-features

- `list` (`Computers in this deployment`).
- `activity` (`Listing files`, `Reading a file`, `Command waiting for approval or to finish`).
- `folders` (`Folders on this computer`, `Choose folder`, `Stop folder access`).
- `egress` (`Leaves directly`, `Egress not reported`).
- `controls` (`Stop browser`, `Reset it`, `Update it`, `Revoke`).

## How to get to it (user POV)

- Admin → Computers.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.
- Supervisor up (port 4500).

- **Open.** `page.goto('/admin/computers')`.
- **Proof.** Screenshot; do not reset others' computers.

## Gotchas

- `Reset it` wipes a Bot's `/workspace` and browser profile.
