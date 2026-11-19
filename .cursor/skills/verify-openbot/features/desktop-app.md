# Desktop app (Tauri)

A macOS and Windows app that runs OpenBot on the person's own machine (sign in with Google or xAI, pick a harness) or connects to an organization's OpenBot; it can let Bots run commands on that computer under approval rules.

Area: Clients and platform. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `desktop/`, `desktop/src-tauri`

## Sub-features

- `welcome` and `provider-picker` (Google, xAI sign-in; `desktop/PROVIDER_OAUTH.md`).
- `harness-picker` choose the Bot framework.
- `organization-sign-in` connect to a company deployment.
- `host-access` commands on your computer (`server/src/host-access`).
- `telemetry` opt-in (`desktop/TELEMETRY.md`).
- `database-reset` local reset screen.

## How to get to it (user POV)

- Install a release build, or `bun run` inside `desktop/` per its package scripts.

## Driving it with Playwright

Preconditions:

- Rust and Tauri toolchain; signing secrets only for release builds.

- **Build.** Desktop CI (`.github/workflows/desktop.yml`) builds on `desktop/**` changes.
- **Drive.** Not covered by Playwright; use the unit tests in `desktop/src/*.test.tsx`.
- **Proof.** Test output.

## Gotchas

- Microphone on macOS needs the entitlement (`desktop/MACOS_MICROPHONE.md`).
- Windows signing uses Azure Key Vault (`docs/windows-signing.md`).
