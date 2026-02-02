## Docker Build (Buildx + Cosign)

Build and push multi-architecture container images using Docker Buildx, then sign them with Cosign when tags are present. Inputs let you control Docker and BuildKit versions as well as the pipeline stage.

### Usage

```yaml
include:
  - component: gitlab.com/shortlink-org/gitlab-templates/docker_build@<version>
    inputs:
      stage: build
      docker_version: "29.2"
```

### Inputs

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `stage` | string | `build` | Stage assigned to `.template_build`. |
| `docker_version` | string | `29.2` | Docker version for DinD and CLI images. |
| `buildkit_version` | string | `v0.26.1` | BuildKit image version for the BuildKit variant. |

### Provided jobs

- `.template_build` — standard Buildx workflow with Cosign signing in `after_script`.
- `.template_build_kit` — alternative using an external BuildKit daemon (`buildctl`) when Docker is unavailable.

### Notes

- Requires `CI_REGISTRY_USER` and `CI_REGISTRY_PASSWORD` to be available for registry authentication.
- The base job always pushes images (`docker buildx build --push`) and signs tags if present. Adjust the script if you require dry runs.
- Use the BuildKit variant when running on environments where privileged DinD is not allowed.

