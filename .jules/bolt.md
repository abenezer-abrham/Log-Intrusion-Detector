## 2026-10-18 - Hoisting Regexes and Single-Pass Line Iteration
**Learning:** Instantiating static regexes inside `analyzeLogs` and using multi-pass `split('\n').filter().forEach()` loops creates significant GC pressure and per-line function call overhead when processing large logs (100k+ lines). Hoisting regexes, pre-flattening pattern rules with severity ranks, and using indexed single-pass `for` loops speeds up analysis by ~33-35%.
**Action:** Always hoist static Regular Expressions and pre-process rule entries outside function bodies when dealing with high-throughput text parsing loops.
