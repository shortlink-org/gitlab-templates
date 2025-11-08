## Dependabot Flow

Trigger Dependabot for Go modules (or another supported package manager) on a schedule. The job reuses the `andrcuns/dependabot-gitlab` image and authenticates with the current project using `CI_JOB_TOKEN`.

### Usage

```yaml
include:
  - component: gitlab.com/shortlink-org/gitlab-templates/dependabot-flow@<version>
    inputs:
      package_manager: gomod
      directory: "/"
```

### Inputs

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `stage` | string | `test` | Stage where the Dependabot job runs. |
| `package_manager` | string | `gomod` | Package manager identifier (e.g., `npm_and_yarn`). |
| `directory` | string | `/` | Repository directory Dependabot should scan. |

### Notes

- The job runs only when `CI_PIPELINE_SOURCE == "schedule"`. Configure a scheduled pipeline to trigger updates.
- Uses `CI_JOB_TOKEN` for GitLab API access; ensure the job has necessary permissions if you customize scopes.
- Packages outside the root directory can be targeted by adjusting the `directory` input.

