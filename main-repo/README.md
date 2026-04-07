# TAAS

High-throughput transformation infrastructure for Kafka Connect pipelines.

## Project Overview

TAAS compiles mapping rules into runtime artifacts and applies them to complex nested payloads inside Kafka Connect pipelines. The goal is to produce sink-ready outputs for PostgreSQL and other downstream systems without requiring bespoke transformation code for every integration.

## What Problem It Solves

- Reduces the operational cost of maintaining pipeline-specific transformation logic.
- Handles nested, claims-style payloads that need deterministic extraction and sink-ready shaping.
- Provides a benchmarkable runtime layer for teams evaluating throughput, sink behavior, and scale limits.

## Benchmark Summary

- Sustained `49,996.71 messages/sec` for `10 minutes` on claims-style payloads of roughly `11 KB`, with matched producer, SMT, and PostgreSQL counters.
- A `100,000 messages/sec` target over `1 minute` achieved about `70,049/sec` SMT throughput and about `70,439/sec` PostgreSQL throughput in-window, then drained the remaining backlog afterward.
- A `200,000 messages/sec` target over `1 minute` scaled to `12` tasks and reached about `121,103/sec` SMT throughput and about `122,283/sec` PostgreSQL throughput in-window.
- A `200,000 messages/sec` target over `5 minutes` with `12` tasks held about `80,041/sec` SMT throughput and about `80,289/sec` PostgreSQL throughput in-window, indicating downstream saturation under longer heavy runs.

Additional detail is available in [docs/benchmark-summary.md](../docs/benchmark-summary.md).

## Current Focus

- Validate multi-worker and higher-scale deployment topologies.
- Improve sustained heavy-load performance across downstream sinks.
- Package benchmark, deployment, and runtime artifacts for repeatable infrastructure evaluation.

## Repo Structure

- `taas-backend/` - control-plane and backend services.
- `taas-smt/` and `taas-smt-e62/` - Kafka Connect SMT runtime and related implementation work.
- `benchmarks/` - benchmark tooling, payloads, and scripts.
- `deploy/` - deployment configurations and environment assets.
- `docs/` - benchmark summaries, runbooks, and supporting documentation.
- `ui/` - operator and mapping workflow UI.

## Getting Started

Getting-started documentation is being consolidated. For now, start with:

1. `docs/benchmark-summary.md` for current performance positioning.
2. `deploy/` for local and benchmark-oriented environment assets.
3. `taas-backend/` for backend services.
4. `taas-smt/` and `taas-smt-e62/` for transformation runtime work.

## Contact

- Repository: [TAAS-LAB/TAAS](https://github.com/TAAS-LAB/TAAS)
- Email: [team@your-domain.com](mailto:team@your-domain.com)
