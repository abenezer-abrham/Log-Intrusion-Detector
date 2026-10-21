# Bolt's Journal

## 2026-10-21 - Log Parsing Hot Path Optimization
**Learning:** Re-creating RegEx objects and iterating arrays via `.forEach()`/`.filter()` inside high-frequency line loops in `detector.js` causes significant GC overhead and CPU cycles when processing large log files (~100k lines).
**Action:** Always hoist static regular expressions (`IP_REGEX`, `STATUS_REGEX`, `HTML_ESCAPE_REGEX`) and pre-flatten constant object structures (`PATTERN_ENTRIES`) at the top-level module scope, and replace multi-pass array operations with single-pass `for` loops.
