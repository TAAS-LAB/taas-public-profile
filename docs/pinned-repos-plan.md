# Pinned Repos Plan

Use the pinned repositories to present TAAS as a focused infrastructure company rather than a collection of unrelated experiments.

## Recommended Pin Order

| Order | Repository | Purpose | Suggested description |
|---|---|---|---|
| 1 | `TAAS` | Main product repo | High-throughput transformation platform for Kafka Connect pipelines. |
| 2 | `taas-benchmarks` | Benchmark evidence | Repeatable throughput benchmarks for TAAS, Kafka Connect, and downstream sink validation. |
| 3 | `taas-deploy` | Deployment story | Deployment and infrastructure configs for TAAS runtime, benchmarking, and scale validation. |
| 4 | `taas-docs` or `taas-deck` | Reviewer-facing collateral | Technical docs, benchmark summaries, and cloud-credit application material for TAAS. |
| 5 | `taas-examples` | Adoption story | Sample mappings and reference pipelines for nested payload transformation. |
| 6 | `taas-control-plane` | Optional platform depth | Control-plane services for artifact compilation, publishing, and runtime distribution. |

## Notes

- Keep the main product repo first. That is the repo most reviewers will open.
- Keep benchmark and deployment repos visible. They make the performance story and infrastructure needs easier to validate.
- If the control-plane repo is not ready to be public, leave it unpinned until it has a clean README and minimal structure.
- Use concise repository descriptions in the GitHub UI. Avoid slogans, superlatives, or claims that exceed the benchmark record.
