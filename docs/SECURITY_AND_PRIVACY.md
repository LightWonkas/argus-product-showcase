# Security and Privacy

## Security posture

The private implementation defines a clear security boundary between:
- internal source data ingestion,
- analysis/persistence,
- and user-facing surfaces.

Public-facing rules in this project:

- No source code or API keys are published here.
- No `.env` file is included.
- Secrets are masked before display in API responses.
- Sessions are cookie-based with secure flags in production-oriented paths.
- Sensitive operations are routed through guarded control paths and authorization.

## Data protection rules

- User/system identifiers from private repos are intentionally omitted.
- No raw private URLs, internal IPs, or machine paths are published.
- No database dumps, logs, or seed data are copied.
- No exact schema definitions/migrations are published.

## Confidentiality controls in this showcase

To keep the repo portfolio-safe:

- Keep markdown evidence at architectural level.
- Use placeholders for UI images until approved.
- Avoid any numeric performance, trade outcomes, or internal benchmark claims.
- Mark partially/experimental features clearly.

## Redaction policy (for screenshots and demos)

- Remove any visible token/API values.
- Remove environment paths, usernames, and hostnames.
- Blur or replace any internal account names or IDs.
- Remove proprietary strategy text, prompt fragments, and private rule lists.
- Replace live price overlays with mocked or delayed context where needed.

## Review checklist for external sharing

Before external sharing:
- Confirm no secret-like patterns remain.
- Confirm images are scrubbed and approved.
- Confirm repository contains only docs, guides, and templates.
