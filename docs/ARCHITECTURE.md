# Architecture

## High-level architecture summary

Argus is organized as a layered, event-driven system with strict interface boundaries between data, analysis, and presentation.

```mermaid
flowchart TB
  subgraph Source Layer
    EX1["External Market Sources"]
    EX2["News / Event Sources"]
  end

  subgraph Ingestion Layer
    I1["Source Registry"]
    I2["Adapters (Market + News)"]
    I3["Normalization Contracts"]
  end

  subgraph Platform Layer
    P1["Quality Gate (schema, gap, duplicate, outlier)"]
    P2["Indicators & Feature Engine"]
    P3["Trigger Engine + Cooldown + Dedup"]
    P4["Event Bus"]
  end

  subgraph Intelligence Layer
    B1["LLM Router / Client seam"]
    B2["Agent stack + context"]
    B3["Policy-aware aggregator"]
  end

  subgraph Decision & Safety Layer
    D1["Guard logic"]
    D2["Portfolio/state snapshots"]
    D3["Outcome and audit journal"]
  end

  subgraph Interface & API Layer
    O1["CLI / Scheduler / Dispatcher"]
    O2["Telegram bot endpoints"]
    O3["Read-only API (status, alerts, analyses, portfolio, news)"]
  end

  subgraph Presentation Layer
    U1["React + Vite dashboard"]
    U2["Copilot / analysis UI components"]
  end

  EX1 --> I1 --> I2 --> I3
  EX2 --> I1
  I3 --> P1 --> P2 --> P3 --> P4
  P4 --> B1 --> B2 --> B3
  B3 --> D1 --> D3
  D1 --> O1
  P4 --> O2
  P2 --> O3
  D2 --> O3
  O3 --> U1
  O3 --> U2
  P3 --> U1
  D3 --> U1
  U1 --> O3
```

## Cross-cutting concerns

- **Storage**: point-in-time persistence for market series and decision records.
- **Configuration**: runtime settings, thresholds, and watchlist values are separated from core logic.
- **Security**: authentication, authorization gates, secret handling, and prompt sanitization practices.
- **Observability**: health checks, status signals, and operational logs used to support debugging and confidence.
- **Resilience**: retry, circuit-breaker behavior, and degraded-mode responses when source quality is insufficient.

## Data flow (high level)

1. Source adapters fetch and normalize incoming market/news data.
2. The quality gate validates shape, freshness, and integrity.
3. Indicators and triggers compute local conditions and event risk.
4. Events move through the bus to analysis, notification, and persistence layers.
5. Analysis output is aggregated and guarded before being surfaced.
6. Read-only API and dashboard present structured state, alerts, and historical outcomes.

## Notes on safety boundaries

This repository intentionally excludes deep internal policy implementation and exact scoring formulas. The architecture emphasizes:

- clear separation of observed data versus advisory output;
- explicit no-hallucination contract when evidence is missing;
- and a strict “no secret exposure” principle in both API and UI surfaces.
