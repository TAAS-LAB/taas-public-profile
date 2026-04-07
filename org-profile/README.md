# TAAS Lab

High-throughput transformation infrastructure for Kafka Connect pipelines.

## Overview

TAAS is a transformation platform built for teams that need to turn complex, nested event payloads into sink-ready records without maintaining custom code for every pipeline. The platform compiles mapping rules into runtime artifacts and applies them inside Kafka Connect flows to produce outputs for PostgreSQL and other downstream systems.

## Why It Matters

Modern integration pipelines often fail at the transformation layer: mappings drift, nested payloads become expensive to manage, and operational overhead grows with each new sink or schema variant. TAAS is focused on making transformation logic repeatable, benchmarkable, and deployable as infrastructure rather than one-off glue code.

## Benchmark Highlights

- Sustained `49,996.71 messages/sec` for `10 minutes` on claims-style payloads of roughly `11 KB`, with matched producer acknowledgements, SMT transformed counters, and PostgreSQL row counters.
- At a `100,000 messages/sec` target for `1 minute`, the system processed about `70,049/sec` through the SMT and about `70,439/sec` into PostgreSQL during the active window, then drained the backlog afterward.
- At a `200,000 messages/sec` target for `1 minute`, scaling to `12` tasks reached about `121,103/sec` SMT throughput and about `122,283/sec` PostgreSQL throughput in-window, with full-drain throughput around `99k/sec`.
- At a `200,000 messages/sec` target for `5 minutes` with `12` tasks, the system held about `80,041/sec` SMT throughput and about `80,289/sec` PostgreSQL throughput in-window, with full-drain behavior around `70k/sec`, indicating downstream saturation under longer heavy runs.

## Why We Need Cloud Credits

- Validate horizontal scale on production-style infrastructure rather than a single constrained test environment.
- Run multi-broker, multi-worker Kafka Connect, and multi-sink benchmarks under controlled configurations.
- Measure sustained throughput, burst recovery, and cost/performance tradeoffs at higher scale.

## Links

- Main repository: [TAAS](https://github.com/TAAS-LAB/TAAS)
- Benchmark summary: [docs/benchmark-summary.md](https://github.com/TAAS-LAB/TAAS/blob/main/docs/benchmark-summary.md)
- Deployment assets: [deploy/](https://github.com/TAAS-LAB/TAAS/tree/main/deploy)
- Benchmark tooling: [benchmarks/](https://github.com/TAAS-LAB/TAAS/tree/main/benchmarks)
- Contact: [team@your-domain.com](mailto:team@your-domain.com)
