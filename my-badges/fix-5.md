<img src="https://my-badges.github.io/my-badges/fix-5.png" alt="I did 5 sequential fixes." title="I did 5 sequential fixes." width="128">
<strong>I did 5 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/intel-codex/commit/c7d99defc4ee6065bc0c05c89342692b60cc359f">c7d99de</a>: fix(sops): re-check ai-vulnerability-evasion against primary sources

- MITRE ATLAS IDs remapped to v2026.10 (T0024.00x -> T0137, T0056 ->
  T0085.003, T0057 -> T0085.002, T0019/T0058 -> T0115, T0010 renamed)
- OWASP LLM Top 10 2026 cited as current, 2025 IDs kept in parentheses;
  model theft folded into Unbounded Consumption, not dropped
- Attack payloads (DAN prompt, encoding bypass strings, extraction prompt
  lists, key-drain script, adversarial-malware function, DoS prompts)
  replaced with method-level test cases, pass criteria and maintained
  probes (garak, promptfoo, PyRIT)
- Tool status: garak CLI flags, Promptfoo now part of OpenAI, Lakera now
  Check Point AI Security, LLM Guard and Rebuff archived
- Research citations, LiRA description, extraction caveats corrected
- Bottom Legal & Ethical Considerations block, footer, Related SOPs
- sop-legal-ethics: US federal AI executive orders (14110 rescinded by
  14148; 14179, 14365, 14409) as the canonical entry
- All April markers re-verified
- <a href="https://github.com/gl0bal01/intel-codex/commit/adaa50075a9aab9e0c8e0a68054e2c0f723c9cca">adaa500</a>: fix(sops): re-check smart-contract-audit against primary sources

- SWC Registry described as unmaintained legacy taxonomy; EthTrust v3 and
  OWASP SC Top 10 2026 named as maintained references
- EIP-6780 SELFDESTRUCT semantics, EIP-4626 rounding, Chainlink
  answeredInRound deprecation, send/transfer deprecation (0.8.31)
- Tooling: Slither --checklist, Foundry invariant config, Aderyn install,
  Certora open source, solana-verifiable-build, Aptos/Sui provers,
  SMTChecker via compiler settings; Manticore archived
- Platforms: Sherlock contests replaced by Audit Engine, Defender shutdown,
  OZ forum security category, dead report links replaced
- New entries: token integration assumptions, ERC-4626 share inflation,
  CosmWasm
- All April markers re-verified
- <a href="https://github.com/gl0bal01/intel-codex/commit/ec1d7fec9a3f3af4ff192c59540eafa45c94acde">ec1d7fe</a>: fix(tools): pin vault-state ages to the committed generation date

Verification-Status.md carries an Age column computed from the current
date, so the CI "generated files are up to date" step failed on any day
after the files were regenerated, with no SOP change at all.

build-vault-state.sh now takes an optional VAULT_STATE_AS_OF date and
does its date arithmetic in UTC; the workflow pins it to the committed
`generated:` date. The check still catches real drift (marker counts,
dates, states), just not the calendar.
- <a href="https://github.com/gl0bal01/intel-codex/commit/94a4bc8a1b19bd40b09007ba00552c76ee7753eb">94a4bc8</a>: fix(sops): re-check cryptography-analysis against primary sources

- NIST IR 8547 (final, Oct 2026): RSA and ECC deprecated after 2030,
  disallowed after 2035; replaces the SP 800-57 2031 cut-off
- X25519MLKEM768 registered under RFC 10024; CNSA 2.0 suite corrected
  (no SLH-DSA), NSM-10 2035 goal
- RsaCtfTool uses --decryptfile and installs with pip install -e .;
  testssl.sh 3.2.4 from the testssl org (--branch 3.2, --fs; no
  --groups); hashcat Argon2 mode 34000; CyberChef offline via release ZIP
- Snippet outputs fixed (pow(2,100,17) = 16, 8051 = 83 x 97); base64
  layer loop no longer over-decodes
- HackTricks and OPSEC links repaired; all April markers re-checked
- <a href="https://github.com/gl0bal01/intel-codex/commit/a6c848e8736e00571cbd5bd842660b07062fbc5e">a6c848e</a>: fix(sops): re-check vulnerability-research and consolidate exploitation material

- Exploitation sections follow a method-and-facts approach: payload,
  ROP, shellcode, heap-grooming and race-exploit code removed; bug-class
  snippets, crash triage, sanitizers and mitigation checks kept
- New Lab Build Flags, glibc Version Limits for Heap Techniques and
  Mitigation Inventory subsections; minimal PoC = harmless win() marker
- x86-64 crash triage reads the saved slot at ret (offset 72 verified);
  AFL++ 5.x uses afl-cc (afl-gcc/afl-clang removed)
- Heap limits per glibc release (2.29, 2.32, 2.34, 2.43 fastbins gone);
  ASLR levels, CET shadow-stack opt-in, FORTIFY_SOURCE=3, kernel config
  renames, canary fork facts corrected
- Privilege escalation keeps enumeration and harmless proof only;
  DirtyPipe build line and SUID shells removed; CVE facts re-checked
- CVE record format 5.2, CNA of Last Resort split (CISA ICS / MITRE),
  CRA reporting from 2026-09-11, CMA s.3 and CWE-119 names
- reverse-engineering Exploit Development reduced to an overview that
  points to Vulnerability Research


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>