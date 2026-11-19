# OpenBot feature map

- `feature-map.html`: the built, self-contained overview (open from disk). Features grouped by area, with a status column and the run and deploy model.
- `feature-map.template.html`: its editable source. Rebuild with `python3 ~/.agent/styles/artifact-system/build.py feature-map.template.html feature-map.html` (the artifact design system lives outside this repo), then put `/* biome-ignore-all lint: generated artifact design-system CSS, rebuilt by build.py */` as the first line inside `<style>` so `bun run lint` stays clean.
- Per-feature recipes (pstack create-verification-skill shape): [`../../.cursor/skills/verify-openbot/features/README.md`](../../.cursor/skills/verify-openbot/features/README.md).

Made Nov 19, 2026 from `main` at `bd4dc949`. There is no public deployment, so every feature is code-only; nothing was launched, signed into or written.
