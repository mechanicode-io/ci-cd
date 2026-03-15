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

| Prefix | SemVer bump |
| ------ | ----------- |
| `fix:` | patch |
| `feat:` | minor |
| `feat!:` / `fix!:` or footer `BREAKING CHANGE:` | major |

## CI/CD

The `tagging-check.yml` workflow runs on every PR. It performs a `semantic-release --dry-run` against the PR branch and posts a **Release Management Report** comment to the PR showing the projected version bump and changelog. The comment is replaced (not appended) on each run.

All files are owned by `@mechanicode-io/ops` (see `CODEOWNERS`).
