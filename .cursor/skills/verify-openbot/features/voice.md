# Voice calls and dictation

Start a voice call with a Bot inside a channel, expand or end it, or dictate into the composer.

Area: Conversations. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/channel/$channelId`, `server/src/voice`, `server/src/dictation`

## Sub-features

- `voice-call` (`Expand voice call`, `End voice call`, `Call settings`, `Call duration`).
- `return-to-chat` (`Return to chat · keep call open`).
- `dictation` speech to text in the composer.

## How to get to it (user POV)

- Channel header call control.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.
- A voice-capable model key and microphone permission.

- **Call.** Start a call; `getByRole('button', { name: 'End voice call' })` appears with `Call duration`.
- **Proof.** Screenshot; not automatable headless without a fake media stream.

## Gotchas

- Needs paid speech/model keys; macOS desktop needs microphone entitlement (`desktop/MACOS_MICROPHONE.md`).
