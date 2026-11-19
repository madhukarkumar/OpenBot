# Self-hosting and deployment

OpenBot is a template, not a hosted product. Locally `scripts/start.sh` runs Postgres, computers, agents and the supervisor in Docker and the server, worker and app on the host. In production one image (`ghcr.io/copilotkit/openbot`) or the Helm chart runs it, with the routines worker as a CronJob.

Area: Clients and platform. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `scripts/start.sh`, `scripts/stop.sh`, `ghcr.io/copilotkit/openbot`, `charts/openbot`, `/health`

## Sub-features

- `local-stack` (`bash scripts/start.sh`, `scripts/stop.sh`).
- `container` one image with optional in-container Postgres.
- `helm` (`charts/openbot`).
- `migrations` (`migrate`; docs/deployment.md).
- `health` (`GET /health` on the API).
- `smoke` (`bun run test:smoke`, an HTTP API journey).

## How to get to it (user POV)

- README → Quick start; docs/deployment.md.

## Driving it with Playwright

Preconditions:

- Docker, Bun, a CopilotKit Intelligence key and a model key (both paid).

- **Health.** `curl -s http://localhost:3001/health` returns `{"status":"ok"}`.
- **Smoke.** `OPENBOT_SMOKE_COOKIE='better-auth.session_token=...' bun run test:smoke` (script sets `OPENBOT_SMOKE=1`; `OPENBOT_API_URL` defaults to `http://localhost:3001`, `OPENBOT_SMOKE_BOT` to `risk-analyst`).
- **Proof.** Health JSON and smoke output.

## Gotchas

- `publish-release.yml` releases only for an in-repo `release/publish/vX.Y.Z` PR with the `release` label.
- The smoke cookie is a live session; never print or commit it.
