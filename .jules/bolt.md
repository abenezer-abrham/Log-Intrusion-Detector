## 2026-10-09 - Optimized Log Processing Engine
**Learning:** Monolithic log processing functions in vanilla JS hit severe performance bottlenecks when allocating intermediate arrays in `.split().filter()` and recreating RegExp / PATTERNS metadata on each run.
**Action:** Hoist static regular expressions and pre-flatten pattern entries outside the function, perform single-pass line iteration, use cached object lookups, lazy-initialize array fields, and use single-pass string replacement maps.
