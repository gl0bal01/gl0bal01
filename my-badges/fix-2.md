<img src="https://my-badges.github.io/my-badges/fix-2.png" alt="I did 2 sequential fixes." title="I did 2 sequential fixes." width="128">
<strong>I did 2 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/volatility-toolkit/commit/ffee829bccb38ed0ee61be405828cdc6a63429e5">ffee829</a>: Fix output-path validation when parent dir doesn't exist

On systems where the candidate parent doesn't exist (e.g. /proc on macOS),
the previous one-liner left the resolved path malformed (e.g. "/bad"
instead of "/proc/bad"), letting the blacklist miss it. Fall back to the
literal argument when cd-then-pwd fails.
- <a href="https://github.com/gl0bal01/volatility-toolkit/commit/1ae7d563c1bbd21eede117246a5d2c54d265b4d6">1ae7d56</a>: Fix mktemp portability in tests for macOS runner

BSD mktemp (macOS) doesn't accept GNU's --suffix flag. Use mktemp -d
plus a staged .raw file inside instead.


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>