<img src="https://my-badges.github.io/my-badges/fix-6+.png" alt="I did 7 sequential fixes." title="I did 7 sequential fixes." width="128">
<strong>I did 7 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/intel-codex/commit/6a335340439eba6243b90bab8d326a578c5a91f5">6a33534</a>: fix(sops): re-check email-bec-forensics against primary sources

- DMARC now cites RFC 9989/9990/9991 (obsolete RFC 7489); BIMI has
  no RFC; RSA key-size guidance per RFC 8301
- Microsoft compauth reason codes, quarantine retention (15 d default),
  Get-MessageTraceV2, Search-UnifiedAuditLog session paging
- ASNs corrected (Mailgun AS396479; AS31034/AS22214 not mail vendors)
- IC3 files regardless of amount; FinCEN RRP 72 h window; no USD
  50,000 FFKC threshold; FOS award limit GBP 455,000
- SWIFT recall via ISO 20022 camt.056 since 22 Nov 2025; Nacha R10/R29,
  Reg J and SEPA recall reason codes re-checked
- Broken commands fixed (gam report gmail, dkimverify, arcverify,
  parsedmarc config, Gmail BigQuery fields); dead links replaced
- All April markers re-verified, corrected or removed
- <a href="https://github.com/gl0bal01/intel-codex/commit/fc0f78d2386e37e343b95592c36c3c3b716d3826">fc0f78d</a>: fix(sops): re-check saas-log-forensics against primary sources

- Purview Audit retention tiers, MailItemsAccessed in Audit (Standard),
  v1.0 Graph auditLogQuery with isRecordCountLimitExceeded check
- Search-UnifiedAuditLog: every search now repeats its ReturnLargeSet
  session until it returns nothing (100-record default, 50,000 cap)
- Mailbox audit check uses org-level AuditDisabled plus bypass
  associations; per-mailbox AuditEnabled always reads True
- Okta Workforce / Auth0 naming and retention; Slack Enterprise plan,
  legal holds; GitHub, GitLab, Google Workspace event names re-checked
- Defender for Office 365 record types split from Defender for Cloud
  Apps; OAuth inventory notes the 20-item $expand cap
- <a href="https://github.com/gl0bal01/intel-codex/commit/e5d6aaabf3981bbae997ded297567fe87299711f">e5d6aaa</a>: fix(sops): re-check cloud-forensics against primary sources

Apply 77 review findings: working aws/az/gcloud commands and detection
queries, Athena now that CloudTrail Lake is closed, hash-before-mount
evidence handling, and the e-Evidence Regulation and SP 800-201.
- <a href="https://github.com/gl0bal01/intel-codex/commit/25c03581abe1339853661d6144c244444924237f">25c0358</a>: fix(sops): re-check forensics-investigation against primary sources

Apply 77 review findings: working acquisition and analysis commands
(dc3dd, AVML, Volatility 3, KAPE, MFTECmd, RegRipper), evidence-safe
backups, FRE 702 (2023), Budapest Art. 29 and the UK FSR Code.
- <a href="https://github.com/gl0bal01/intel-codex/commit/5e041b123b4f98e025a88198984c03131f09bf5e">5e041b1</a>: fix(sops): re-check the crypto and darkweb SOPs against primary sources

Apply 135 review findings across mixer-tracing, blockchain-investigation and
darkweb-investigation: current case outcomes and sanctions status, dead
endpoints, Tor Safest guidance, and consistent reporting channels.
- <a href="https://github.com/gl0bal01/intel-codex/commit/cde5ebc95e2fe5a94fd24e67b894101e2b341fb2">cde5ebc</a>: fix(sops): re-check the investigation-core SOPs against primary sources

Apply 197 review findings across sensitive-crime, collection-log, entity-dossier,
image-video, web-dns-whois, financial-aml and Discord; align related SOPs on
Report Fraud, the UK Sanctions List, OFAC links and the Etherscan V2 API.
- <a href="https://github.com/gl0bal01/intel-codex/commit/6adaaa696117ddd77ed76b2830a622f83c9cb11e">6adaaa6</a>: fix(sops): re-check legal-ethics and opsec-plan against primary sources

Apply 109 findings, fix the VPN kill switches and current law (AI Act omnibus,
DUAA 2025, AU privacy tort, DMCA (b)(18)), and align related SOPs on Nitter,
Old Reddit, NIST 800-88r2 and the REPORT Act.


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>