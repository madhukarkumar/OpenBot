# Identity providers (SSO)

Register a company SAML or OIDC provider by email domain, issuer and client id.

Area: Admin. Status (Nov 19, 2026): **Code-only (no public deployment exists; local launch is documented but needs paid keys and was not run)**.

Where it lives: `/admin/identity-providers`, `/api/admin/identity-providers`

## Sub-features

- `register` (`Email domain`, `Issuer`, `Client ID`).
- `list` registered providers.

## How to get to it (user POV)

- Admin → Identity providers.

## Driving it with Playwright

Preconditions:

- Local stack up with `bash scripts/start.sh` (app `http://localhost:3010`, API `http://localhost:3001`), `.env` from `.env.example` with `OPENBOT_SINGLE_USER=true` so every request is one administrator.

- **Open.** `page.goto('/admin/identity-providers')`; `Email domain`.
- **Proof.** Screenshot; do not register a real IdP.

## Gotchas

- A wrong domain routes real people to the wrong IdP.
