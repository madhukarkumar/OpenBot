---
name: verify-openbot
description: The map of every user-facing OpenBot feature and how to drive each one against a local stack. Use when verifying a change end to end, writing a browser or API test, finding which route or screen owns a feature, or checking what a feature needs (keys, Docker, third-party accounts) before running it. Don't use for copy (openbot-copy), screen layout (openbot-screen-layout) or data access (openbot-data-access).
---

# Verify OpenBot

The feature map lives in `.cursor/skills/verify-openbot/features/` so Cursor and Claude agents share one copy.

1. Read `.cursor/skills/verify-openbot/features/README.md`: run model, baseline preconditions, driving conventions, and the index of features by area.
2. Open the one feature file you need. Each has four sections: Sub-features, How to get to it (user POV), Driving it with Playwright, Gotchas.
3. The human overview is `docs/feature-map/feature-map.html`.

Rules: run only against a local stack (`bash scripts/start.sh`, `OPENBOT_SINGLE_USER=true`). Never sign in with a real account, connect a real vendor, send SMS, or print the smoke-test session cookie. When routes change, update the matching feature file and the index.
