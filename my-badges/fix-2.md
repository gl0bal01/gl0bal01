<img src="https://my-badges.github.io/my-badges/fix-2.png" alt="I did 2 sequential fixes." title="I did 2 sequential fixes." width="128">
<strong>I did 2 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/pai-hermes/commit/1cf74e7a6e8957218bf505431288d2edc7a2da4f">1cf74e7</a>: fix(uninstall): rewrite SC2015 A&&B||C as if/then for shellcheck CI

The gateway-restart cleanup used `is-active && restart || true`, which
shellcheck flags (SC2015): the `|| true` can fire when is-active succeeds
but restart fails. CI runs plain shellcheck (info level), so it broke the
build. Use an explicit `if is-active; then restart || true; fi`.
- <a href="https://github.com/gl0bal01/pai-hermes/commit/db16521227221652be03745e9d1f3deb0bfb76b5">db16521</a>: fix(pai-watch): make the upstream watcher work out-of-box

The skill defaulted PAI_PROJET_ROOT to /opt/pai-projet (rarely the real
clone root) and PAI_PROPOSALS_DIR to /var/lib/pai-anywhere/proposals —
owned by pai-anywhere's `pai` user and unwritable by the Hermes gateway,
which runs as the human user. A fresh install therefore ran the hourly
watcher against a non-existent root and silently dropped every proposal.

- Default PAI_PROPOSALS_DIR to ${XDG_STATE_HOME:-$HOME/.local/state}/
  pai-hermes/proposals (always gateway-writable; created on demand).
- install.sh auto-detects PAI_PROJET_ROOT (parent of the checkout),
  narrows PAI_WATCH_SOURCES to repos that exist, writes all three to
  $HERMES_HOME/pai-hermes.env, and wires it as an EnvironmentFile= drop-in
  on the systemd --user gateway (prints instructions otherwise).
- uninstall.sh reverses the env file + drop-in.
- Skill/doc defaults realigned; CHANGELOG updated.


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>