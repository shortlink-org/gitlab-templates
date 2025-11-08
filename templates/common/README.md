## Common Pipeline Defaults

This component centralizes shared pipeline defaults such as Docker-in-Docker settings and a friendly pipeline name. It’s designed to be included ahead of build or deploy components so they inherit consistent DinD behavior.

### Usage

```yaml
include:
  - component: gitlab.com/shortlink-org/gitlab-templates/common@<version>
    inputs:
      pipeline_name: "My Project Pipeline"
```

### Inputs

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `docker_driver` | string | `overlay2` | Docker storage driver used by DinD services. |
| `docker_host` | string | `tcp://docker:2375` | Docker engine endpoint shared with jobs. |
| `pipeline_name` | string | `Shortlink pipeline` | Friendly name exposed to downstream jobs. |

### Notes

- Include this component before other components that expect Docker to be available.
- Override inputs only when a project needs different Docker configuration. Otherwise keep the secure defaults.

