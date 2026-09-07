# Engineering Highlights

## Design principles implemented in product

- **Layer isolation by contract**
  - Distinct boundaries for ingestion, platform rules, analysis, decision, and interface.
  - Reduces blast radius and improves testability.

- **Dependency inversion for external services**
  - Networked providers are injected behind typed seams.
  - Keeps local tests deterministic and prevents provider-specific coupling.

- **Data-first reliability**
  - Quality checks and provenance metadata are used before analysis paths.
  - Missing or stale data is represented explicitly, not silently coerced.

- **Observability-first behavior**
  - Health/status, error boundaries, and operational state are surfaced.
  - Audit-oriented logging supports decision traceability.

- **Cost-conscious AI integration**
  - Routed AI calls include budget guards and role-based routing.
  - Analysis is not continuously model-driven.

## Hardening patterns

- Retry with bounded behavior and controlled backoff.
- Circuit-breaker behavior for degraded source behavior.
- Idempotency patterns for repeated events and event replay.
- Secrets stored outside repository content and never echoed in public responses.
- Session/authorization controls for API and dashboard access.

## Engineering trade-offs

- **Advisory-first vs execution-first**  
  A strict advisory posture improves safety and reviewability in Phase 1.

- **Read-only dashboard first**  
  The dashboard is intentionally designed to avoid introducing a second ungoverned control plane.

- **Polling fallback where needed**  
  Polling is used where stream reliability was lower than complexity threshold; this is explicitly identified as active work-in-progress.

## What is intentionally omitted from public narrative

- Exact model prompts and calibration logic.
- Full strategy math and scoring thresholds.
- Private runtime keys, endpoints, and internal IDs.
- Private schema SQL definitions and migration content.

## Why this matters for clients

- The architecture is suitable for regulated or sensitive environments where:
  - operational traceability,
  - bounded automation,
  - and controlled AI usage
  are required.
