## Helm Deploy

Deploy Helm releases with `helm secrets upgrade` and optional environment metadata. Includes auxiliary jobs for rollback, history, and environment teardown.

### Usage

```yaml
include:
  - component: gitlab.com/shortlink-org/gitlab-templates/helm_deploy@<version>
    inputs:
      provider: "contabo"
      namespace: "prod"
      release_name: "shortlink"
      helm_path: "charts/shortlink"
      kube_context: "contabo-prod"
```

### Inputs

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `provider` | string | — | Identifier for the backing Kubernetes provider (used in environment name). |
| `namespace` | string | — | Target Kubernetes namespace. |
| `release_name` | string | — | Helm release name. |
| `helm_path` | string | — | Path to the Helm chart directory. |
| `helm_arg` | string | `""` | Additional CLI arguments (e.g., extra values files). |
| `kube_context` | string | — | Fully qualified kube context. |
| `environment_url` | string | `""` | Optional environment URL shown in GitLab. |

### Notes

- `deploy` job auto-discovers `*.values.yaml` files in the chart directory and passes them to Helm.
- Environment name is derived from `provider/release_name`; a manual `drop` job removes the environment.
- `rollback` and `history` jobs provide manual operational fallbacks.
- Ensure Helm secrets and SOPS plugin requirements are satisfied by including the `helm` base component first.

