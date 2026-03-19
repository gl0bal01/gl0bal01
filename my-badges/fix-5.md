<img src="https://my-badges.github.io/my-badges/fix-5.png" alt="I did 5 sequential fixes." title="I did 5 sequential fixes." width="128">
<strong>I did 5 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/discord-osint-assistant/commit/3925ae93ecd024a2abf0016ff777b5230bc04452">3925ae9</a>: fix(security): address all Docker security audit findings

HIGH fixes:
- F10: Stop leaking secrets to child processes — safeSpawn now uses
  minimal env (PATH, HOME, LANG only) instead of full process.env
- F1: Pin Dockerfile base image to node:18.20-slim
- F2: Multi-stage build — builder stage for npm ci, clean runtime stage
- F9: Create docker-compose.yml with no-new-privileges, cap_drop ALL,
  read_only fs, tmpfs mounts, memory/PID limits
- F12: Lazy-init AWS Rekognition client with credential validation

MEDIUM fixes:
- F15: Add getSafeAxiosConfig to rekognition.js downloads
- F4: Change default tool paths from /root/ to /opt/ (non-root accessible)
- F25: Move JWT temp folder inside /app/temp/
- F26: Move ghunt results inside /app/temp/
- F23: Add 50MB output file size limit to safeSpawnToFile
- F17: Add Trivy image scanning to CI pipeline
- F18: Pin GitHub Actions to SHA commits
- F21: Tighten npm audit to --audit-level=moderate

LOW fixes:
- F8: Expand .dockerignore (admin scripts, CI configs, docs)
- F24: Add 1MB stderr buffer cap to safeSpawn/safeSpawnToFile
- F27: Add startup cleanup for orphaned temp files >24h old

45 tests passing, 0 lint errors.

Co-Authored-By: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
- <a href="https://github.com/gl0bal01/discord-osint-assistant/commit/04a3afe2e1746c1fc0c72ea9980c26808054532e">04a3afe</a>: fix(security): eliminate all SSRF bypasses, error leaks, and rate limit race

SSRF hardening (H1, H2, H3, M4):
- Fix IPv4-mapped IPv6 bypass (::ffff:127.0.0.1 now detected as private)
- Check both A and AAAA DNS records (not just one fallback)
- Add connect-time IP validation via custom http.Agent (eliminates DNS rebinding)
- Re-validate each redirect hop in redirect-chain.js
- Apply safe agents to all axios calls in 7 URL-accepting commands

Error leak fixes (M1, M2, M3):
- aviation.js: stop leaking API error status/data to users
- nike.js: stop leaking err.message in HTML report creation
- jwt.js: stop leaking raw stderr to users

Rate limit fix (M5):
- Make check-and-record atomic to prevent concurrent request bypass
- Remove separate recordUsage call from index.js

Tests: 45 passing (+2 new IPv4-mapped IPv6 tests)

Co-Authored-By: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
- <a href="https://github.com/gl0bal01/discord-osint-assistant/commit/f283831ac1fec1c8dcc405ceb5d1caf89c980f48">f283831</a>: fix: commit lockfile, use npm ci for reproducible builds, tighten audit

- Remove package-lock.json from .gitignore and commit it
- Fresh lockfile resolves undici to 6.24.1 — npm audit now shows 0 vulnerabilities
- Dockerfile: switch from npm install to npm ci for reproducible builds
- CI: switch to npm ci, tighten audit level from critical to high
- Both production blockers from readiness assessment are now resolved

Co-Authored-By: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
- <a href="https://github.com/gl0bal01/discord-osint-assistant/commit/83c675cc34f58ead62b6cb618772147cc2349b42">83c675c</a>: fix(security): override undici to 6.24.1 to patch all CVEs

discord.js and @discordjs/rest pin undici@6.21.3 which has 6 known
CVEs (HTTP smuggling, CRLF injection, WebSocket crashes, unbounded
decompression). Override forces 6.24.1 which patches all of them.

Note: npm audit still reports the vulns because it reads declared
ranges, not installed versions. Actual installed version is 6.24.1
(verified via node_modules). discord.js loads and works correctly.

Co-Authored-By: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
- <a href="https://github.com/gl0bal01/discord-osint-assistant/commit/163a39e1044efa2f36780585c470d1f400a20db8">163a39e</a>: fix: address all code review findings (C1-C3, I1-I8, S4-S8)

Critical:
- C1: Add SSRF protection to exif.js (was missed)
- C2: Fix favicons.js error.message leak
- C3: Document DNS rebinding limitation in ssrf.js

Important:
- I1: Standardize || false to ?? false across 16 command files (21 occurrences)
- I3: Replace local chunk functions in nuclei.js with utils/chunks imports
- I4: Fix config.js || to ternary for empty string env vars
- I5: Escape URL in ghunt.js generateLinkCard href attribute
- I6: Stop leaking SSRF validation messages in 5 commands
- I7: Fix Dockerfile healthcheck to verify node process is running
- I8: Move recordUsage before command.execute to prevent concurrent bypass

Suggestions:
- S4: Remove stale playwright reference from monitor.js comment
- S7: Sanitize dork.js attachment name
- S8: Add Node 22 to CI matrix

Co-Authored-By: Claude Opus 4.6 (1M context) <noreply@anthropic.com>


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>