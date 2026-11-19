# Bot frameworks (AG-UI harnesses)

Bots are any AG-UI agent. The repo ships harness images per framework and examples for LangGraph, Mastra and Pydantic AI; external agents register by URL.

Area: Clients and platform. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `agent-*`, `examples/langgraph-bot`, `examples/mastra-bot`, `examples/pydantic-ai-bot`

## Sub-features

- `default-bot` (`agent-bot`, port 4200).
- `langgraph` (`agent-langgraph`, 4201).
- `picked-harness` (`agent-harness`, 4202, compose profile `harness`).
- `examples` LangGraph, Mastra, Pydantic AI.
- `external-ag-ui` register an endpoint (docs/coworkers.md).

## How to get to it (user POV)

- `/bots` → Create a Bot → Where will your Bot run?

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Check.** `docker compose ps` shows the agent containers.
- **Proof.** A message answered by the picked harness.

## Gotchas

- `agent-bot` is skipped when `BOT_PROVIDER=anthropic` (OpenAI-only sample).
