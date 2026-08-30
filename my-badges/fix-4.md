<img src="https://my-badges.github.io/my-badges/fix-4.png" alt="I did 4 sequential fixes." title="I did 4 sequential fixes." width="128">
<strong>I did 4 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/selfhosted-secrets-stack/commit/111aa4ababcaa4c4f10d8a511b4863a2f2eca3e3">111aa4a</a>: fix: unblock CI — CVE-gate remediation and gitleaks permissions

- gitleaks: grant pull-requests:read so gitleaks-action can list PR
  commits on pull_request events (403 'Resource not accessible by
  integration' on every PR)
- passbolt: 5.13.0 -> 5.15.0-1-ce (fixes PHP CVE-2026-17543/17544) and
  move to a custom build (passbolt/Dockerfile) that apt-upgrades the
  digest-pinned upstream, clearing the util-linux CVE-2026-53612..53615
  family (fixed in 2.41.5-0+deb13u1, shipped after upstream's build)
- caddy: refresh stale builder-alpine digest (re-pushed 2026-08-20 with
  patched Go toolchain — clears Go stdlib CVEs in the binary), apk
  upgrade the runtime (c-ares/curl alpine fixes), and pin vulnerable
  Go module deps (x/net v0.58.0, x/text v0.41.0, grpc v1.83.1) via an
  explicit go-build (xcaddy --with replace breaks on golang.org/x/*
  downgrades)
- infisical: v0.161.12 -> v0.162.24 (report-only image, keep fresh)
- hadolint job lints both Dockerfiles; scan workflow builds all custom
  images via docker compose build
- <a href="https://github.com/gl0bal01/selfhosted-secrets-stack/commit/98f3d56a9396626b7f065c6b337d68ceccfe2efa">98f3d56</a>: fix: harden disaster recovery restore path
- <a href="https://github.com/gl0bal01/selfhosted-secrets-stack/commit/e2b38bff4104ec5f910de5ee7b586c108b3e3858">e2b38bf</a>: fix: image CVE gate — bump stale pins, codify scan policy

- bump mariadb 11.8.8 + passbolt 5.13.0-1-ce digests (upstream
  rebuilds fix flagged HIGH/CRITICAL), infisical v0.161.9 -> v0.161.12
- scan.sh: skip /usr/local/bin/gosu (every official mariadb/postgres
  image ships gosu with stale Go stdlib; runs once at start to drop
  root, no network — flagged code paths unreachable)
- scan.sh: infisical image REPORT-ONLY — remaining findings are in
  upstream-bundled node_modules/agent binaries no pinnable tag fixes;
  loud warning instead of permanent red gate
- SECURITY.md: document 'Image CVE gate policy' (rationale,
  compensating controls, review cadence)

Verified: full scripts/scan.sh run green locally on all 7 images.
- <a href="https://github.com/gl0bal01/selfhosted-secrets-stack/commit/2f0ab7c3187c8b8523552b126abc86c2ee520a2d">2f0ab7c</a>: fix: security review findings (backup auth, ufw bypass, signup)

- backup/restore: MYSQL_PWD (MARIADB_PWD is not read by mariadb
  clients — every dump/import failed auth; verified live)
- harden.sh: install DOCKER-USER rules via /etc/ufw/after.rules;
  Docker-published ports bypass ufw INPUT, docs corrected everywhere
- compose: drop no-op Infisical ALLOW_SIGNUP*/SMTP_SECURE (absent
  from v0.161.9 env schema); use SMTP_REQUIRE_TLS/SMTP_IGNORE_TLS;
  document Server Admin Console signup lockdown in GO-LIVE
- ci: trigger on master (was main — CI never ran on push)
- restore.sh: resolve COMPOSE_PROJECT_NAME from .env + normalize
  like compose-go before volume detection
- redis: runtime-expanded requirepass (not in inspect Cmd),
  healthcheck via REDISCLI_AUTH (no password on argv)
- passbolt healthcheck: require HTTP 200 (curl -f passed 3xx)
- systemd: make timer-install templates User=/paths; fix %h misuse
- backups: empty replication placeholders, warn when no off-box
  target; SECURITY.md: LUKS required for seized-disk threat
- bump pre-commit hooks (gitleaks v8.30.1, shellcheck v0.11.0)


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>