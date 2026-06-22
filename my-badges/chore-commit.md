<img src="https://my-badges.github.io/my-badges/chore-commit.png" alt="I did a little housekeeping! 🧹" title="I did a little housekeeping! 🧹" width="128">
<strong>I did a little housekeeping! 🧹</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/spectrum-gene-explorer/commit/9957b7dd4fbbd447f63ada3639b50803430105a1">9957b7d</a>: chore: production readiness pass — type safety, security, infra

- Add explicit generic type parameters for mypy strict mode
- Fix all 15 mypy errors across app.py, scoring.py, data_loader.py, traits.py, build_dataset.py
- Add input file existence validation to build_dataset.py CLI
- Harden Dockerfile: non-root appuser + HEALTHCHECK
- Remove pytest from requirements.txt (dev-only dep)
- Expand .gitignore with .mypy_cache, .ruff_cache, *.egg-info, dist, build, .omo
- Add LICENSE, pyproject.toml, Dockerfile, .dockerignore, CI workflow


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>