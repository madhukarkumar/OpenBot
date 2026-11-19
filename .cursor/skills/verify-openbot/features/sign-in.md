# Sign-in and sign-in providers

People sign in with Google, Microsoft or Okta from the environment, or with a company SAML or OIDC provider routed by email domain; on a laptop `OPENBOT_SINGLE_USER=true` skips sign-in and admits every request as one administrator. Every page under the app redirects to `/sign` without a session.

Area: Access and onboarding. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/sign`, `/api/me`, `/api/auth/*`

## Sub-features

- `single-user` admits everyone as one admin when no provider is configured (laptop default).
- `social-sign-in` signs in with Google, Microsoft or Okta (Better Auth).
- `email-domain-sso` routes an email domain to a registered SAML or OIDC provider.
- `brokered-return` resumes a brokered authorization (`/sign?flow_id=`).
- `session-gate` sends every `_authed` page to `/sign` without a session.
- `desktop-org-sign-in` uses the system browser and PKCE when the desktop app points at an organization OpenBot.

## How to get to it (user POV)

- Open the app URL; without a session it lands on `/sign`.
- Desktop app connection screen → Organization OpenBot URL.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.
- For provider sign-in: unset `OPENBOT_SINGLE_USER` and set one provider's client id and secret (needs a real OAuth client, so not for unattended runs).

- **Single-user.** `page.goto('http://localhost:3010/')` lands on `/` (or `/onboarding` the first time) without a sign-in page.
- **Gate.** With a provider configured and a fresh context, `page.goto('/bots')` ends on `/sign`.
- **API.** `curl -s -o /dev/null -w '%{http_code}' http://localhost:3001/api/me` returns 401 without a cookie.
- **Proof.** Screenshot of `/sign` with the provider buttons, plus the 401.

## Gotchas

- Never sign in with a real account from an agent; use single-user mode locally.
- Localhost is not a secure context; `Secure` cookies need HTTPS in a real deployment.
- The smoke test needs a `better-auth.session_token` cookie (`OPENBOT_SMOKE_COOKIE`); treat it as a credential and never log it.
