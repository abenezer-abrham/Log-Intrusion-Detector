## 2026-10-28 - Avoid Object.entries Allocations in Hot Log Analysis Loops
**Learning:** Calling `Object.entries(PATTERNS)` inside an iteration loop processing 100k log lines creates 100k array allocations and tuple objects. Pre-flattening `PATTERNS` at top-level into a static array `PATTERN_ENTRIES` with precomputed severity ranks completely eliminates object allocation overhead in hot paths.
**Action:** Always pre-flatten static configuration maps into array constants with precalculated metadata when iterating over large collections or streams.
