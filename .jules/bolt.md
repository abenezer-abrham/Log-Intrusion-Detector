## 2026-10-12 - [Avoid Object.entries inside per-line log parsing loops]
**Learning:** Calling `Object.entries()` inside per-line loops creates $O(N \times P)$ array allocations for $N$ log lines and $P$ threat patterns. Pre-flattening patterns into a static `PATTERN_ENTRIES` array outside the loop eliminates hundreds of thousands of intermediate object and array allocations.
**Action:** Always hoist pattern definitions and pre-calculate entries/ranks when processing sequential streams or lines of log text.
