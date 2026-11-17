<img src="https://my-badges.github.io/my-badges/fix-2.png" alt="I did 2 sequential fixes." title="I did 2 sequential fixes." width="128">
<strong>I did 2 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/chainmap/commit/8f89b57de450854073c0e967e484d0ab33562228">8f89b57</a>: fix(i18n): "faux jeton" wording; refresh edge tooltips on locale switch

applyLocale now re-projects the graph view so flag text in edge labels and
tooltips follows the language. Integration tests assert the FR tooltip and
that the '*'-only OFAC fixture address exists before use.
- <a href="https://github.com/gl0bal01/chainmap/commit/708bf0d32ac34a23e33060772151366d35318e3a">708bf0d</a>: fix(data-build): fail closed on unfetchable sources and OFAC tag drift

- --verify-sources aborts (nothing written) when a cited page cannot be
  fetched, listing each URL and row count; only `absent` rows are excluded
- parseOfacXml throws when a valid 0x address sits under a non-allowlisted
  Digital Currency tag, naming the tag(s)
- reject a curated "*" row whose address is on the SDN, so the OFAC entry
  keeps its source/added
- chain-specific rows that become sanctioned append "; OFAC SDN list,
  published <date>" to their source (snapshot date visible in Source)
- atomic write (tmp + rename); KNOWN_ADDRESSES_OUT redirects output for tests
- CLI tests: one scenario fetch stub preloaded for every case, temp output,
  new GitHub non-200 and verify fetch-failed/absent cases
- regenerate data (13 source strings gain the OFAC publish date)


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>