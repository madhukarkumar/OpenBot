# OpenBot verification map

This directory maps every user-facing feature of OpenBot (`madhukarkumar/OpenBot`, a fork of `CopilotKit/OpenBot`) on `main` at `bd4dc949` (Oct 22, 2026). It follows the pstack create-verification-skill feature-map shape. Read this index first, then use the matching feature file as the recipe.

Sources: app routes in `app/src/routes` (TanStack Router), API in `server/src/app.ts`, the README `Main surfaces` table, and `docs/` (architecture, coworkers, routines, deployment, plugins).

## Run and deploy model

- OpenBot is a template, not a hosted product. There is no public deployment of this fork; `copilotkit.ai/openbot` is a marketing page.
- Local: `cp .env.example .env`, `bun install`, set the CopilotKit Intelligence key and a model key (`OPENAI_API_KEY`), then `bash scripts/start.sh`. App `http://localhost:3010`, API `http://localhost:3001`. Docker runs Postgres (pgvector), `agent-computer` (4100), `agent-bot` (4200), `agent-langgraph` (4201) and the supervisor (4500); the host runs the server, the routines worker and the app. `bash scripts/stop.sh` stops it.
- Production: one image `ghcr.io/copilotkit/openbot` (docs/deployment.md) or the Helm chart `charts/openbot`; the routines worker runs as a CronJob.
- Releases: `publish-release.yml` publishes only when a merged in-repo `release/publish/vX.Y.Z` PR carries the `release` label. `ci.yml` runs on PRs and on push to main.

## Baseline preconditions

- Local stack up, `.env` with `OPENBOT_SINGLE_USER=true` so every request is one administrator and no sign-in is needed.
- Both keys cost money; every Bot turn calls the model and Intelligence. Use short test prompts.
- Writes (Bots, rules, routines, credentials) go to the local Postgres volume only. Never point a run at a shared deployment.

## Driving conventions

- Harness: Playwright (`playwright-core` is a root dependency; there is no browser e2e suite yet). Base URL `http://localhost:3010`.
- API journey: `OPENBOT_SMOKE_COOKIE='better-auth.session_token=...' bun run test:smoke` runs `tests/smoke/journey.test.ts` against `OPENBOT_API_URL` (default `http://localhost:3001`). The cookie is a live session; never print or commit it.
- Prefer ARIA roles and accessible names (most labels are props such as `aria-label`), then `data-testid`. Confirm names with an ARIA snapshot before hard-coding.

## Proof and skip reporting

- Capture the action and the resulting state (screenshot plus ARIA snapshot); for governed actions also capture the `/admin/audit` row.
- Report a feature that needs a third-party account (Slack, Teams, Twilio, Composio, Arcade, OAuth providers) as unverified with the reason.

## Feature entry contract

Each feature file starts with an H1 and one paragraph, a status line and where it lives, then exactly four H2 sections: `Sub-features`, `How to get to it (user POV)`, `Driving it with Playwright` (starting with `Preconditions:`), and `Gotchas`.

## Status key

- **Code-only**: present on `main`; not exercised against a running deployment. All features are code-only on Nov 19, 2026.

## Features (39)

### Access and onboarding (2)

- [Sign-in and sign-in providers](./sign-in.md). People sign in with Google, Microsoft or Okta from the environment, or with a company SAML or OIDC provider routed by email domain; on a laptop `OPENBOT_SINGLE_USER=true` skips sign-in and admits every request as one administrator.
- [Onboarding](./onboarding.md). A first-time person is held on `/onboarding` until they finish it: it explains that each Bot has its own computer, lets them pick a Bot or make one, and shows the self-host message.

### Conversations (5)

- [Home, channel list and search](./home-and-channels.md). The home screen starts a conversation and lists channels with unread markers; the sidebar holds New conversation, search and the Bots.
- [Channel conversation with a Bot](./channel-conversation.md). A one-to-one channel with a coworker: send messages and files, get answers as components rather than prose, invoke skills with `/`, stop a run, and see what the Bot needs from you.
- [Group conversations](./group-conversations.md). Two or more Bots (and people, invited by email) in one channel; Bots can hand work to each other.
- [Direct Bot chat](./direct-bot-chat.md). Chat with one Bot directly beside its computer; `?agent=<id>` selects which.
- [Voice calls and dictation](./voice.md). Start a voice call with a Bot inside a channel, expand or end it, or dictate into the composer.

### Bot computer (3)

- [Watching a Bot's screen and activity](./bot-screen-and-activity.md). Each Bot works on its own computer (Chromium plus `/workspace`).
- [Take control and hand back](./take-the-wheel.md). A person can take control of the Bot's computer (for a login, captcha or a fiddly step) and hand it back; the Bot can also ask for help.
- [Signing a Bot in to a website](./bot-website-sign-in.md). When a Bot hits a login wall it sends a private sign-in request; the person opens it and signs in by hand, uses a saved login, or enters a verification code.

### Bots (7)

- [Bots directory and creating a Bot](./bots-directory.md). Lists Bots by Needs you, Pinned, Yours, Shared with you and Hidden; creates a Bot, choosing where it runs and optionally registering an external AG-UI agent.
- [A Bot's page](./bot-page.md). One Bot's home: what it can do for you, what needs you, background research and activity, with links to its settings tabs.
- [Goals (responsibilities)](./bot-goals.md). Standing goals a Bot is responsible for; the Bot works toward them proactively.
- [Routines](./routines.md). Standing instructions a Bot runs on a schedule.
- [Reach (Slack, Teams, SMS and other destinations)](./bot-reach.md). Where a Bot can reach people outside the app: Slack and Microsoft Teams through the OpenTag pairing (`server/src/delivery/opentag.ts`), SMS through Twilio, and push to devices; plus connecting a conversation to a destination.
- [Bot memory and background research](./bot-memory-research.md). What a Bot remembers and which app sources it learns from, plus background research it does on its own.
- [Bot access, setup and sharing](./bot-access-setup-sharing.md). Per-Bot configuration: which skills and tools it has and which Bots it can ask; its identity, AG-UI connection and tool key; and who it is published or assigned to.

### Approvals and governance (3)

- [Approvals (personal, per-Bot and team)](./approvals.md). Before a Bot acts it can be made to ask.
- [Boundaries (CEL policy)](./admin-boundaries.md). Administrator policy written as CEL rules over every governed browser, file, shell and MCP action: what Bots may never do and what they may otherwise do.
- [Audit log](./admin-audit.md). Every governed action, approval and admin change, with filters and CSV export; retention is configurable.

### Capabilities (3)

- [Connections (apps a person connects)](./connections.md). Each person connects the apps an administrator enabled (MCP servers, Composio apps, Arcade tools, Google Drive, Notion, Gmail) and sees each connection's tools and actions.
- [Skills (personal and workspace)](./skills.md). Instructions Bots load on demand.
- [Personal memory](./personal-memory.md). Facts a person asks Bots to remember about them, shared across their Bots; stored in CopilotKit Intelligence.

### Settings (4)

- [Preferences and standing instructions](./preferences.md). Personal settings: dark theme, standing instructions every Bot follows, and keyboard shortcuts.
- [Saved logins](./saved-passwords.md). Logins a person saves so Bots can sign in to websites without seeing the secret (used by sign-in requests).
- [Notifications and devices](./notifications.md). Devices that get push notifications (desktop and mobile) and recent deliveries.
- [Components (gallery, admin and playground)](./components.md). Generative UI components Bots answer with.

### Admin (8)

- [Admin home and status](./admin-overview.md). The administrator landing page linking every admin surface, with deployment status and the tenant package (agents, brand, model, skills, knowledge YAML).
- [Saved credentials (team)](./admin-credentials.md). Team credentials Bots can use without seeing them, encrypted at rest.
- [Computers](./admin-computers.md). Every computer in the deployment (Bot containers from the supervisor, and people's own computers via the desktop app): what each is doing, approved folders, egress, and controls to stop, reset, update or revoke.
- [Plugins (MCP, Composio, Arcade)](./admin-plugins.md). Administrators register MCP servers and brokers (Composio, Arcade), enable apps, and grant tools per Bot; shared accounts let one connection serve a team.
- [Automatic learning](./admin-learning.md). Bots contribute conversations to a Learning container that proposes skills; an admin reviews and publishes them to Bots.
- [People and roles](./admin-people.md). Who is in the deployment, their role (admin or member) and access.
- [Identity providers (SSO)](./admin-identity-providers.md). Register a company SAML or OIDC provider by email domain, issuer and client id.
- [Enterprise controls](./admin-enterprise.md). Deployment-wide switches: require SSO, only approved MCP servers, a model allowlist, and action recording.

### Clients and platform (4)

- [Desktop app (Tauri)](./desktop-app.md). A macOS and Windows app that runs OpenBot on the person's own machine (sign in with Google or xAI, pick a harness) or connects to an organization's OpenBot; it can let Bots run commands on that computer under approval rules.
- [Mobile app (Expo)](./mobile-app.md). A phone companion: conversations, Bots, approvals, the Bot's computer, memory, plugins, routines and rules, with push notifications.
- [Bot frameworks (AG-UI harnesses)](./agent-harnesses.md). Bots are any AG-UI agent.
- [Self-hosting and deployment](./self-host-deploy.md). OpenBot is a template, not a hosted product.

## Redirect-only routes

`/agents`, `/approvals`, `/memory`, `/skills`, `/responsibilities`, `/reachability`, `/team-bots`, `/group/new`, `/capabilities`, `/settings/memory` redirect to their current pages and are covered by the features above.
