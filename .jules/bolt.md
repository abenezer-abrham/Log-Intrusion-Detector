# Bolt's Performance Journal ⚡

## 2026-11-05 - Log Parsing and Heuristic Pattern Matching Bottleneck
**Learning:** In client-side log inspection tools, repeatedly executing `Object.entries(PATTERNS)` inside inner line-processing loops creates substantial GC pressure and overhead (~129ms out of ~326ms for 92,000 lines). Pre-flattening rule signatures with precalculated severity ranks, hoisting regex constants, skipping intermediate array allocations from `.split().filter()`, and avoiding intermediate empty arrays for unflagged lines cuts parse-and-analysis time by ~50%.
**Action:** When scanning large datasets (e.g. log lines, tokens, records) against static rules in JavaScript, hoist all static regular expressions, pre-flatten rule maps into an array with precalculated static properties, and use index-based single-pass iteration with lazy allocations.
