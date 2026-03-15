# Notes

We utilize [Conventional Commits](https://www.conventionalcommits.org/) messages and automated tagging via [Semantic Versioning](https://semver.org/) for managing helm chart releases.

When making changes that affect the helm chart, use these prefixes:

- `fix:` represents bug fixes, correlates to a SemVer patch
  - Example: `fix: correct indentation in values.yaml`
- `feat:` represents a new feature, correlates to a SemVer minor
  - Example: `feat: add support for custom environment variables`
- Breaking changes (SemVer major) can be indicated in two ways:
  - `feat!:` or `fix!:` with the `!` indicating a breaking change
  - Adding `BREAKING CHANGE:` in the commit message footer
  - Example:

    ```text
    feat!: change default authentication method
    BREAKING CHANGE: Authentication now requires different configuration format
    ```
