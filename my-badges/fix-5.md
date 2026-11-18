<img src="https://my-badges.github.io/my-badges/fix-5.png" alt="I did 5 sequential fixes." title="I did 5 sequential fixes." width="128">
<strong>I did 5 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/chainmap/commit/148b20fac0d78a3241672089d88c67a4c04b64a1">148b20f</a>: fix(i18n): French TronGrid privacy wording; token box names TRC-20

"n'est contacté qu'une fois Tron choisi" replaces the dangling
infinitive, and the token-transfer checkbox lists TRC-20 in English and
French.
- <a href="https://github.com/gl0bal01/chainmap/commit/929a4a81f955bef3ff3c1bafd5fe2d2b1934b9e0">929a4a8</a>: fix(tron): a logged TronGrid limit must be canonical

The query-log sanitiser now refuses a limit with a leading zero such as
007, so a workspace entry rebuilds to the exact URL that was sent.
- <a href="https://github.com/gl0bal01/chainmap/commit/3fbf33f1660b7e71d9748a3e92eefe3660395676">3fbf33f</a>: fix(tron): only a digit-string TRC-20 value is determinate

A JSON-number value (rounded by JSON.parse) or any non-digit string
leaves tokenDecimal empty, so the amount reads as indeterminate instead
of a silent 0 or a rounded number. A TRC-10 transfer without asset_name
is labelled TRC10:? instead of TRC10:undefined.
- <a href="https://github.com/gl0bal01/chainmap/commit/19bb16a9d7d2fe804c093688287d9a9051ed8f0a">19bb16a</a>: fix(tron): never lowercase a base58-looking workspace root

Only a valid 0x root is lowercased; anything that is neither a Tron
address nor a 0x address is saved as typed.
- <a href="https://github.com/gl0bal01/chainmap/commit/687147baeb1a8995cad1fbbddc33218835153c15">687147b</a>: fix(tron): never probe or load a Tron node on other chains

checkOtherChains and loadOnChain return at once for a Tron node. The
details panel already hides both actions; main.js exports the two as a
test seam so the guards are covered.


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>