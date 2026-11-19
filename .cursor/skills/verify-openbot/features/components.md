# Components (gallery, admin and playground)

Generative UI components Bots answer with. People browse the gallery; admins grant components to Bots and draft new ones in the playground before publishing.

Area: Settings. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/settings/components-gallery`, `/settings/components-gallery/$name`, `/admin/components`, `/admin/components/$name`, `/admin/playground`

## Sub-features

- `gallery` browse and preview.
- `admin-components` grant per Bot.
- `playground` (`Save draft`, `Publish`).

## How to get to it (user POV)

- Settings → Components gallery.
- Admin → Components, Playground.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Gallery.** `page.goto('/settings/components-gallery')`; open one.
- **Playground.** `page.goto('/admin/playground')`; `Save draft` (no `Publish`).
- **Proof.** Screenshots.

## Gotchas

- `Publish` makes a component available to every granted Bot.
