# Benchmark Summary

This summary captures the benchmark results currently suitable for a GitHub profile, repository README, and cloud credit application material. It keeps claims limited to measured runs and avoids cross-tool comparisons that were not validated under identical conditions.

## Sustained Benchmark

### 50k/sec for 10 minutes

- Workload: claims-style payloads of roughly `11 KB`
- Producer acknowledgements: `49,996.71 messages/sec`
- SMT transformed rate: `49,979.33 messages/sec`
- PostgreSQL row rate: `49,979.33 rows/sec`
- Result: the run stayed effectively matched end to end for the full `10-minute` window

### 200k/sec for 5 minutes with 12 tasks

- Producer acknowledgements: `199,931.23 messages/sec`
- In-window SMT rate: `80,040.54 messages/sec`
- In-window PostgreSQL rate: `80,288.81 rows/sec`
- Full-drain behavior: about `70k/sec`
- Result: the system remained operational under the heavier sustained load, but the downstream path saturated over the longer run

## Burst Benchmark

### 100k/sec for 1 minute

- Producer acknowledgements: `99,925.83 messages/sec`
- In-window SMT rate: `70,048.91 messages/sec`
- In-window PostgreSQL rate: `70,438.55 rows/sec`
- Backlog behavior: backlog accumulated during the active window and drained afterward

### 200k/sec for 1 minute

- Best observed in-window scaling at `12` tasks: about `121,103/sec` SMT and about `122,283/sec` PostgreSQL
- Full-drain behavior for the run: about `99k/sec`
- Result: short-window throughput increased substantially with additional task parallelism, but end-to-end completion still depended on draining the backlog after the peak interval

## Heavy Benchmark Scaling Table

`200k/sec` target, `1-minute` window, heavy payload scenario

| Tasks | Producer ack rate | In-window SMT rate | In-window PostgreSQL rate | End-of-window lag | Notes |
|---|---:|---:|---:|---:|---|
| 6 | 199,843.34/s | 90,590.45/s | 91,522.82/s | 7,145,706 | Stable run with substantial backlog left at window end |
| 9 | 199,853.92/s | 114,949.05/s | 116,001.30/s | 5,742,909 | Improved parallel throughput with lower residual lag |
| 12 | 199,866.75/s | 121,102.91/s | 122,283.13/s | 5,362,794 | Best in-window throughput in the current scaling set |

## Interpretation

- The `50k/sec` sustained run shows balanced end-to-end capacity for this workload on the current benchmark setup.
- The `100k/sec` and `200k/sec` short-window tests show that the platform can absorb higher burst load than the sustained baseline, but backlog management becomes part of the overall throughput story.
- The `200k/sec` five-minute run indicates that the long-run ceiling is currently constrained by downstream sink capacity rather than transformation logic alone.
