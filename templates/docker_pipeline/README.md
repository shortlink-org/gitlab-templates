# Docker Pipeline

Opinionated pipeline composition that builds container images, scans them with GitLab’s container scanning component, and verifies Cosign signatures. It reuses the shared `common` and `docker_build` components.

## Usage

```yaml
include:
  - component: gitlab.com/shortlink-org/gitlab-templates/docker_pipeline@<version>
```

## Provided stages

| Stage | Jobs |
| --- | --- |
| `.pre` | inherited from `common` (environment inspection) |
| `build` | `build` (extends `.template_build`) |
| `security` | `container_scanning`, `verify_image` |

## Notes

- The `build` job tags branch builds with `CI_COMMIT_REF_SLUG` to satisfy downstream scanning and verification.
- `container_scanning` includes GitLab’s official component (`container-scanning@main`). Pin to a tag when moving towards production use.
- `verify_image` runs Cosign verification and is marked `allow_failure: true`; tighten this policy once signatures are mandatory.
- Update the `TODO` in the template when the security job is finalized and remove the comment.
