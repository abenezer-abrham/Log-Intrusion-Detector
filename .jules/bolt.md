## 2026-09-11 - [Log Parsing Optimization]
**Learning:** Hoisting regular expressions, replacing higher-order array methods (`.forEach`, `.filter`) with standard index-based `for` loops, lazy-allocating intermediate arrays, and caching object lookups inside tight log processing loops significantly reduces garbage collection overhead and execution time in client-side JS log engines.
**Action:** When processing large text inputs/logs in JS, avoid creating intermediate arrays with `.filter()` or `.map()` and hoist static regular expressions outside of loop/function scopes.
