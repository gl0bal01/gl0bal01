<img src="https://my-badges.github.io/my-badges/fix-2.png" alt="I did 2 sequential fixes." title="I did 2 sequential fixes." width="128">
<strong>I did 2 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/discord-osint-assistant/commit/17aa4c7b321b68364f492aff26c60e0c84136983">17aa4c7</a>: fix: address code review findings

- Convert health.js from exec to safeSpawn for tool availability checks
- Add shell:false + SIGKILL fallback to linkook.js spawn call
- Fix error.message leaks in maigret, sherlock, exif (generic msgs now)
- Fix XSS in nike.js HTML report with escapeHtml
- Remove global flag from regexes in containsMaliciousPatterns (.test() bug)

Co-Authored-By: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
- <a href="https://github.com/gl0bal01/discord-osint-assistant/commit/581319ce216aae61f59bb8c4f0dfb9d645617c37">581319c</a>: fix: Nike token in-memory cache, remove last dotenv call

- Replace plaintext Nike token file storage with in-memory cache + TTL
- Remove redundant dotenv call from pappers.js

Co-Authored-By: Claude Opus 4.6 (1M context) <noreply@anthropic.com>


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>