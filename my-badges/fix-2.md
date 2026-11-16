<img src="https://my-badges.github.io/my-badges/fix-2.png" alt="I did 2 sequential fixes." title="I did 2 sequential fixes." width="128">
<strong>I did 2 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/chainmap/commit/8eb1cbbd0b580c0f8ec65a6291acd1ba24b76833">8eb1cbb</a>: fix(load-older): graph-chain reads, error/sampling status, cursor guard

Known-label, category, risk, search and CSV lookups use the graph's chain
(dataChain) instead of the selector. loadOlder counts per-type fetch errors
and the status reports them; a load shows the sampling banner. advance()
ignores non-numeric blockNumbers. Page size re-renders details on input,
not blur. Clearer history/complete/plan-required wording (en+fr).
- <a href="https://github.com/gl0bal01/chainmap/commit/89a0d88fbc8057c6f1387502e8ac5091b5444f37">89a0d88</a>: fix(graph): contrasting border so the more-history dashes are visible


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>