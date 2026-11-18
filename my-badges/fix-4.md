<img src="https://my-badges.github.io/my-badges/fix-4.png" alt="I did 4 sequential fixes." title="I did 4 sequential fixes." width="128">
<strong>I did 4 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/chainmap/commit/c801c069ab1e81040c01cc7adc3c22654bc24db9">c801c06</a>: fix(tron): the Etherscan client refuses the Tron chain id

createEtherscanClient and setChainId throw for 728126428 before any
fetch, so no Tron address or Etherscan key can reach api.etherscan.io
through a mis-routed call.
- <a href="https://github.com/gl0bal01/chainmap/commit/892428bcbb0311cd0292ad95a56add990eed55d7">892428b</a>: fix(tron): show the TronGrid notice while the graph holds a Tron node

Load older on a Tron node contacts TronGrid whatever chain is selected,
so the notice and key field follow the graph's chain set too (scan,
workspace or demo load, prune, reset).
- <a href="https://github.com/gl0bal01/chainmap/commit/4acc21f6a13b5c239842f34db1321ff9f85e7492">4acc21f</a>: fix(tron): fill a short page that still carries a fingerprint

A short TronGrid page with meta.fingerprint is not the end of the data:
follow it (at most 10 paced, logged hops) so Load older does not mark
the address as complete.
- <a href="https://github.com/gl0bal01/chainmap/commit/46dcba5c150625c2e99247540ea41ba78ed0a215">46dcba5</a>: fix(tron): legacy v1/v2 workspaces never fall back to Tron

A file that predates Tron takes the selected EVM chain, else the stored
EVM chain, else Ethereum, so loading it with Tron selected no longer
drops every node and wipes the graph.


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>