# Bolt's Journal - Critical Performance Learnings

## 2026-03-30 - Client-Side Log Parsing Throughput in Hot Loops
**Learning:** In browser-based heuristic log analyzers like LogWatch, iterating over raw lines using `Object.entries()` inside per-line loops causes heavy GC overhead from array and closure allocations. Hoisting regex definitions, pre-flattening pattern entries with numeric severity ranks, caching hash lookups, and tracking summary counts inline delivers ~40% faster parsing throughput (~560k+ lines/sec vs ~337k lines/sec) while keeping 100% exact parity.
**Action:** When scanning repetitive line-based formats in JavaScript, avoid per-line `Object.entries()`, closure callbacks, and redundant post-processing filters; compute summaries during the primary scan pass.
