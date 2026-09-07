# Features and Evidence Level

## Verified features

| Feature | Status | Evidence source |
|---|---|---|
| Layered package structure (`core`, `ingestion`, `platform`, `brain`, `decision`, `interface`, `api`, `storage`, `observability`) | Implemented | Repository file map |
| Watch scheduler + layered cadence | Implemented | `interface/scheduler.py`, `interface/watch_loop.py`, `interface/sessions.py` references |
| Ingestion adapters for market and event sources | Implemented | `src/argus/ingestion/*` |
| Data quality gate (schema, gap/outlier/duplicate checks) | Implemented | `platform/quality.py` |
| Indicator and trigger pipeline | Implemented | `platform/indicators.py`, `platform/triggers.py` |
| Event stream abstraction | Implemented | `platform/event_bus.py` |
| Point-in-time persistence | Implemented | `storage/sqlite.py`, `storage/README`-level storage layout references |
| LLM routing seam with provider abstraction | Implemented | `brain/llm.py`, `brain/router.py` |
| Model/provider role mapping in settings | Implemented | `api/settings_models.py`, `brain/router.py`, docs |
| Cost guard and budget cap | Implemented | `brain/budget.py` |
| Analysis journal / outcome tracking | Implemented | `storage/*`, API analysis endpoints |
| Telegram control plane (commands, authorization, notifier) | Implemented | `interface/*` files and docs |
| Read-only dashboard API + auth | Implemented | `api/app.py`, `api/security.py`, `web/src` |
| Settings read/update with masked secrets | Implemented | `config/env_writer.py`, `settings` API routes |

## Partially implemented features

| Feature | Status | Notes |
|---|---|---|
| Real-time event push to dashboard widgets | Partially implemented | Polling is used for several surfaces; streaming is documented as continuing work |
| Full portfolio integration depth | Partially implemented | Portfolio views exist; integration depth varies by available live source coverage |
| Production hardening across all optional integrations | Partial | Some optional integrations are planned and/or behind available checks |
| Multi-provider runtime execution stack | Partial | Some providers are live, others are configured as planned/roadmap |

## Planned features (documented)

| Feature | Status | Scope |
|---|---|---|
| Full execution gateway with exchange/frequency control | Planned | Intentional Phase 2 execution boundary |
| Freqtrade/bridge-style dry-run integration | Planned | Documented in roadmap |
| Advanced embedding/RAG stack in memory layer | Planned | Noted as roadmap continuation |
| Streaming frontend UX improvements | Planned | Explicitly noted for later milestones |

## Experimental items

| Feature | Status | Notes |
|---|---|---|
| Internal experimentation prompts and deep-model behavior experiments | Experimental | Described in internal docs with explicit caution; not presented as production behavior |

## Demonstration-only content

- This showcase repository itself is demonstration-focused.
- All screenshots are currently placeholders until approval.
- Placeholder claims are used where private data capture is required for publication.
