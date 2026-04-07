# TAAS

High-throughput transformation infrastructure for Kafka Connect pipelines.

## Overview

TAAS is an early-stage infrastructure product focused on the transformation layer of event-driven data systems. It compiles mapping rules into runtime artifacts and applies them to complex nested payloads in Kafka Connect-style pipelines, producing sink-ready outputs for PostgreSQL and other downstream data platforms.

This public repository is intended to present the product, benchmark evidence, and operating focus for technical reviewers, startup programs, and cloud credit applications.

## Why It Matters

Transformation logic is often the least reusable and least observable part of a data pipeline. As payloads become more nested and downstream requirements become stricter, teams end up maintaining brittle, sink-specific code paths that are hard to scale and expensive to operate.

TAAS is being built to make that layer more repeatable, benchmarkable, and production-oriented, with emphasis on throughput, sink compatibility, and operational safety.

## Benchmark Highlights

### Sustained

- Tested on realistic claims-style payloads around `~11 KB` each.
- Sustained `50k messages/sec` for `10 minutes`.
- Producer, SMT, and PostgreSQL counters matched for the full benchmark window.
- No additional drain was required after the run completed.

### Burst

- At `100k/sec` for `1 minute`, the system achieved about `70k/sec` in-window.
- Backlog accumulated during the burst and drained afterward.

### Heavy-Load Scaling

- At `200k/sec` for `1 minute`, higher task counts reached about `121k/sec` SMT throughput in-window and about `122k/sec` PostgreSQL throughput in-window.
- Full-drain throughput for that short heavy run reached about `99k/sec`.
- At `200k/sec` for `5 minutes` with `12` tasks, the system sustained about `80k/sec` in-window and about `70k/sec` to full drain.
- The longer heavy run indicated downstream saturation under extended load rather than a cleanly balanced end-to-end state.

Additional benchmark context: [benchmark deck link]

## Why We Need Cloud Credits

- Validate horizontal scale on production-style infrastructure rather than a single constrained test setup.
- Test multiple brokers, multiple Connect workers, and multiple downstream sink configurations.
- Measure sustained throughput, burst recovery, and cost/performance behavior at larger scale.
- Establish clearer operating envelopes for heavy-load and long-duration workloads.

## Code Availability

TAAS is currently a private-code startup project. Core implementation, internal deployment assets, and runtime code are not public at this stage.

This repository is intentionally public as a product and benchmarking profile for reviewers who need a concise view of what TAAS does, what has been measured so far, and why additional infrastructure credits are needed.

## Contact / Links

- GitHub organization: [GitHub org link]
- Product repository profile: [TAAS public profile link]
- Benchmark materials: [benchmark deck link]
- Contact: [email]

## Summary

TAAS is building a transformation platform for Kafka Connect pipelines with an emphasis on high-throughput runtime execution, downstream sink compatibility, and disciplined benchmark validation. The public profile is limited by design, but the benchmark record already supports serious infrastructure evaluation and larger-scale testing.
