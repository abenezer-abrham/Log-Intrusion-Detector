## 2026-09-11 - Hoist pattern entries & avoid per-line array allocations in log analyzer engine
**Learning:** Re-evaluating `Object.entries(PATTERNS)` on every single line of log input generates massive GC overhead and object allocations. Pre-flattening static patterns and hoisting regexes outside `analyzeLogs` yields significant execution speedup (~23% faster on 100k lines).
**Action:** Always pre-flatten static configuration/pattern objects and hoist static regexes outside hot parsing/scanning loops.
