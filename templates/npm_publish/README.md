## npm Publish (GitLab Registry)

Publish a package to the project’s GitLab npm registry with provenance disabled. Supports semantic versioning for tags and canary releases from the `main` branch.

### Usage

```yaml
include:
  - component: gitlab.com/shortlink-org/gitlab-templates/npm_publish@<version>
    inputs:
      stage: release
      package_path: "packages/app"
```

### Inputs

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `stage` | string | `build` | Stage for the publish job. |
| `package_path` | string | `.` | Relative path to the package root. |

### Notes

- Automatically configures `.npmrc` for the project namespace using `CI_JOB_TOKEN`.
- Uses `pnpm` (via Corepack) to install, version, and build before publishing.
- Tag pipelines (`CI_COMMIT_TAG`) publish `latest`; pushes to `main` publish timestamped canary builds.
- Safe to include alongside other components that prepare build artifacts or run tests.

