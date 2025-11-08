## pnpm Cache

Reusable cache definition for pnpm’s content-addressable store, keyed by `pnpm-lock.yaml`.

### Usage

```yaml
include:
  - component: gitlab.com/shortlink-org/gitlab-templates/pnpm_cache@<version>

build:
  extends: .pnpm_cache
  script:
    - corepack enable
    - pnpm install
```

### Notes

- Adds `.pnpm-store` to the job cache, keyed by the lockfile so cache updates only when dependencies change.
- Extend `.pnpm_cache` in jobs running pnpm commands to speed up installs.

