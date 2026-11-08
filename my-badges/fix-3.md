<img src="https://my-badges.github.io/my-badges/fix-3.png" alt="I did 3 sequential fixes." title="I did 3 sequential fixes." width="128">
<strong>I did 3 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/devbox/commit/051a74101ff2ec5a680ccc2f52bebfa2e3286776">051a741</a>: fix: working backup and restore, real security checks, helper fixes

- backup.sh finds volumes by compose label (it skipped every volume),
  pauses users for consistency, streams encryption, keeps N archives
- new restore.sh: validates before stopping, keeps host configuration
- security-check.sh checks wildcard publishes, UFW, effective sshd,
  container hardening and digest pins
- rotate-ollama-auth.sh no longer writes a $$-escaped hash
- helpers resolve DEVBOX_HOME from their location (sudo sets HOME=/root)
- htb-vpn, exegol, diagnose and laptop helper fixes; drop harden-* modules
- <a href="https://github.com/gl0bal01/devbox/commit/fd15fc28878f467a97e4ff4e90a6d964e9b3507c">fd15fc2</a>: fix: native COMPOSE_FILE chain, fail-closed binds, Traefik file access

- each service .env sets COMPOSE_FILE so the digest lock always applies
  (it was ignored in the default HTTP mode)
- TAILSCALE_IP and WEBUI_SECRET_KEY fail closed instead of binding 0.0.0.0
- Traefik reads 0640 auth middlewares via group_add (cap_drop ALL made
  them unreadable); ACME state in a named volume Traefik owns
- logs to stdout with daemon-level rotation; drop rate limit and the
  isolating-nothing ollama-net; optional NVIDIA GPU overlay
- bump Ollama 0.40.10 and Open WebUI 0.12; locks keep tag@digest
- <a href="https://github.com/gl0bal01/devbox/commit/80a1535543f1c62f42bf8a018ad00e95da41a311">80a1535</a>: fix: rebuild setup.sh around preflight, signed vendor repos and safe SSH lockdown

- read-only preflight collects every error before the first host change
- Tailscale and mise from vendor apt repos, signing keys pinned by
  fingerprint (scripts/lib/pins.sh); dev tools via mise with verified
  backends; replaces a download manifest whose SHAs were placeholders
- SSH lockdown last: 00- drop-in checked with sshd -t / sshd -T,
  socket-activation-aware restart, sshd must listen before UFW changes,
  full rollback (including the legacy drop-in); port kept on upgrades
- credentials persisted once, derived files re-rendered every run
- shared library and contract v3 for setup and installed helpers


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>