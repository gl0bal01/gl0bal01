<img src="https://my-badges.github.io/my-badges/fix-2.png" alt="I did 2 sequential fixes." title="I did 2 sequential fixes." width="128">
<strong>I did 2 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/devbox/commit/5fe74d27bb91ff3a65e2787ddcf4f8930717cd4f">5fe74d2</a>: fix: isolate the smoke test from an installed stack

The scratch copy kept the installed project names, so running it on a
devbox host recreated the live containers and `down -v` deleted their
volumes (models, Open WebUI database). Run under devbox-smoke-* project
names and refuse to start when any devbox container already exists.
- <a href="https://github.com/gl0bal01/devbox/commit/1062bd1605339d454805122e4dc12bcb041efd00">1062bd1</a>: fix: give Open WebUI room to boot; e2e dumps diagnostics on failure

Open WebUI's first boot downloads and loads its RAG embedding model and
peaks around 850 MB, so the 1g cap left no headroom and the first-run
health check failed on the GitHub runner. Default to 2g
(OPENWEBUI_MEM_LIMIT), allow a 120s start period probed every 5s, and
print container state and logs whenever e2e.sh fails.


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>