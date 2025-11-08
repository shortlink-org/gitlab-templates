## Kubernetes CRD Apply

Apply custom resource definitions with server-side apply and ApplySets. The job expects manifests that can be safely pruned and a Kubernetes context reachable by the runner.

### Usage

```yaml
include:
  - component: gitlab.com/shortlink-org/gitlab-templates/crd@<version>
    inputs:
      kube_context: "my-cluster"
      manifest: "k8s/crds"
```

### Inputs

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `kube_context` | string | — | Required kubectl context to target. |
| `applyset` | string | `default` | ApplySet suffix used for pruning coordination. |
| `manifest` | string | `k8s` | Path to the CRD manifest file or directory. |

### Notes

- The job enables `KUBECTL_APPLYSET` and uses `kubectl apply --server-side` with pruning.
- Ensure the runner has credentials for the specified context (via variables, mounted kubeconfig, or Vault). 
- Consider disabling the job in production branches if CRDs are managed elsewhere.

