## Helm Base

Reusable Helm job configuration that installs `helm-secrets`, SOPS, and GnuPG support, while keeping jobs interruptible and retryable.

### Usage

```yaml
include:
  - component: gitlab.com/shortlink-org/gitlab-templates/helm@<version>

helm-lint:
  extends:
    - .job_template_helm
  script:
    - helm lint charts/my-app
```

### Inputs

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `stage` | string | `action` | Stage assigned to `.job_template_helm`. |

### Notes

- Installs `helm-secrets` and SOPS (`v3.10.2`) for rendering encrypted values.
- Imports a GPG key from `$GPG_TOKEN`; configure the variable in your project settings or integrate with a secret manager.
- Extend this template for deploy, rollback, or helm-specific automation across projects.

