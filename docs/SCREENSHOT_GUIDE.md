# Screenshot Guide

Capture screenshots only after redaction review. Keep files in `assets/screenshots/`.

## Recommended screenshots for README

1. **System status overview**
   - **File:** `argus-status-overview.png`
   - **What it should show:** top-level dashboard health, active/critical source state, budget gauge, hit rate.
   - **Redactions:** user identifiers, session cookies, hostnames/IPs.

2. **Watchlist and alert feed**
   - **File:** `argus-watch-alerts.png`
   - **What it should show:** watchlist rows with freshness state and alert cards.
   - **Redactions:** any internal IDs and raw timestamps if they include machine/user context.

3. **Portfolio and risk context**
   - **File:** `argus-portfolio-risk.png`
   - **What it should show:** current holdings view, mark-to-market summary, and no hidden actions.
   - **Redactions:** real position sizes or balances if not authorized for public sharing.

4. **News and intelligence journal**
   - **File:** `argus-news-feed.png`
   - **What it should show:** sanitized news stream and analysis summary row.
   - **Redactions:** source headers that include private subscription accounts or internal API metadata.

5. **Settings and model mapping**
   - **File:** `argus-settings-models.png`
   - **What it should show:** masked secrets, editable non-secret knobs, and model/provider mapping UI.
   - **Redactions:** secret values, tokens, full keys, hidden config paths.

## Capture process

1. Use a fresh local browser session.
2. Open each target at normal desktop size (recommended `1440x900`) and a second mobile crop (`390x844`) for responsive validation.
3. Replace all sensitive values with placeholders if automatic redaction is not guaranteed.
4. Save only in PNG format.
5. Add each file to `assets/screenshots/` only after security review.

## README insertion order

- `argus-status-overview.png`
- `argus-watch-alerts.png`
- `argus-portfolio-risk.png`
- `argus-news-feed.png`
- `argus-settings-models.png`

## Notes

- If no approvals are available, use placeholders in the README and keep this guide as the publishing checklist.
