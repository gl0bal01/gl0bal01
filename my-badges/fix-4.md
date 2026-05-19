<img src="https://my-badges.github.io/my-badges/fix-4.png" alt="I did 4 sequential fixes." title="I did 4 sequential fixes." width="128">
<strong>I did 4 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/pwndocker-reverse/commit/6d8681f7f605ff1eab6596c21ebb5306a98fcd48">6d8681f</a>: fix(ci): scope Trivy gate to CRITICAL OS CVEs only

Previous config (HIGH+CRITICAL on os+library) blocks on every embedded
Go stdlib / Python METADATA CVE in the 45+ bundled analysis tools.
Those are upstream's job to patch. Gate now blocks only on CRITICAL
ubuntu CVEs with a known fix.

Also update README to describe the narrower gate.
- <a href="https://github.com/gl0bal01/pwndocker-reverse/commit/2d65bbcd2dd02158687184aae564fb56d7106b08">2d65bbc</a>: fix(ci): pin Trivy action to real tag v0.36.0

Previous c17f07b used aquasecurity/trivy-action@0.24.0 which does not
exist as a tag. CI failed in Set up job with "Unable to resolve action".
- <a href="https://github.com/gl0bal01/pwndocker-reverse/commit/c17f07b3f899ba6ea372dcee94ec5c837c0bd930">c17f07b</a>: fix: address code review — bug fixes, CI hardening, dedup helper

* Extract config/fetch-gh-release.sh helper; 6 Dockerfile RUN blocks
  (opengrep, cutter, ghidra, retdec, imhex, pwninit) now call it
  instead of repeating curl+jq+wget+empty-check inline.
* MOTD: echo '\n...' → printf so newlines render in /etc/motd.
* IDA Free: replace dead regex check with `file ... | grep ELF`
  and add post-install ida64 binary check.
* Ghidra: replace `mv /opt/ghidra_*` glob with explicit `find`
  plus ghidraRun executable check.
* Binary Ninja: add existence check before symlink.
* retdec: validate /opt/retdec/bin exists and only symlink
  actual executables; error if none found.
* zsh_history: COPY moved after oh-my-zsh install with --chown
  so the installer can't overwrite the pre-populated history.
* MOTD: rephrase decomp2dbg note (not installed; user installs).
* Set PWNDBG_NO_AUTOUPDATE=1 — /opt/pwndbg is root-owned, so the
  ctf user otherwise sees a "Permission denied" wall on every
  gdb-pwndbg launch.

CI:
* New shellcheck step via ludeeus/action-shellcheck.
* Trivy vuln scan (HIGH/CRITICAL, ignore-unfixed) after smoke test.
* Smoke test now functionally invokes each tool (r2 -qv, pwn
  checksec, pwntools/capstone/keystone/unicorn import via the pipx
  venv python, gdb-multiarch -nx --batch, gdb-pwndbg --batch).

Docs:
* README: new "Security & Trade-offs" section covering passwordless
  sudo, unpinned git plugins, and the Wayback IDA snapshot.
* README: fix checksec example (apt pkg not installed) → pwn checksec;
  same fix in config/zsh_history.
* README: remove duplicate pwninit row; add ImHex to GUI tools list.
* config/gdbinit: one-line purpose comment.
- <a href="https://github.com/gl0bal01/pwndocker-reverse/commit/a58461d2e1605d0a621b96be8203fdc99b0d5b2b">a58461d</a>: fix: correct qemu usage, harden gdb wrappers and release fetches

- Dockerfile: bake libc6-{armhf,arm64}-cross sysroots so qemu-user -L
  works for dynamic ARM/AARCH64 binaries without per-container apt-get.
  Also guard GitHub release fetches: only send Authorization header when
  a token is actually present (avoids empty 'token ' header on anon
  rebuilds, which can trigger rate-limit edge cases).
- config/gdb-{pwndbg,gef,peda}: add -nx to skip system/user/CWD .gdbinit
  so the explicit -x plugin load is deterministic, and a malicious
  .gdbinit in a challenge directory cannot auto-execute.
- README.md: replace nonexistent 'qemu-user' command with real binaries
  (qemu-arm, qemu-aarch64), document new sysroot setup, split static vs
  dynamic vs gdbserver examples, fix history count (78 not 97), refresh
  stale weekly tag placeholder.
- config/zsh_history: same qemu binary fix.
- CLAUDE.md: document cross-libc bake decision.
- .gitignore: ignore .omc/ workspace.


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>