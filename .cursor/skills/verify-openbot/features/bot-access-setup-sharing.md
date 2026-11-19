# Bot access, setup and sharing

Per-Bot configuration: which skills and tools it has and which Bots it can ask; its identity, AG-UI connection and tool key; and who it is published or assigned to.

Area: Bots. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/bots/$agentId/access`, `/bots/$agentId/setup`, `/bots/$agentId/sharing`

## Sub-features

- `skills-and-access` (`Skills and access`, `Bots it can ask`).
- `identity` (`Identity`).
- `connection` (`Connection`, AG-UI endpoint).
- `tool-key` (`Key for tools`).
- `publish` (`Published`).
- `assign-groups` (`Assign to groups`).

## How to get to it (user POV)

- Bot page → Access, Setup, Sharing.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Access.** `page.goto('/bots/<id>/access')`; `Bots it can ask`.
- **Setup.** `page.goto('/bots/<id>/setup')`; `Identity`, `Connection`.
- **Sharing.** `page.goto('/bots/<id>/sharing')`; `Published`.
- **Proof.** One screenshot per tab.

## Gotchas

- `Key for tools` is a secret; never screenshot it revealed.
- Sharing changes are visible to other people on a real deployment.
