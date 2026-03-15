# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Local Development

```sh
pip install -r requirements.txt
pre-commit install --hook-type commit-msg
uvicorn hello-world.main:app --reload
```

## Commit Conventions

All commits must follow [Conventional Commits](https://www.conventionalcommits.org/). This is enforced locally via `.pre-commit-config.yaml` and validated in CI via the `tagging-check` workflow.

| Prefix                                          | SemVer bump |
| ----------------------------------------------- | ----------- |
| `fix:`                                          | patch       |
| `feat:`                                         | minor       |
| `feat!:` / `fix!:` or footer `BREAKING CHANGE:` | major       |

## CI/CD

**On pull requests** — `tagging-check.yml` performs a `semantic-release --dry-run` and posts a **Release Management Report** comment showing the projected version bump and changelog. The comment is replaced (not appended) on each run.

**On merge to `main`** — `release.yml` runs `semantic-release` to tag the release, then builds and pushes the Docker image to `ghcr.io/<org>/ci-cd` tagged with both the version and `latest`.

Both workflows post/commit as the org GitHub App bot, configured via `GIT_APP_OP_APP_ID`, `GIT_APP_OP_PRIVATE_KEY` (secrets), and `GIT_APP_OP_OWNER`, `GIT_APP_OP_NAME` (variables).

All files are owned by `@mechanicode-io/ops` (see `CODEOWNERS`).
