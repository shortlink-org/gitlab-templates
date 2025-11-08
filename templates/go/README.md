## Go Job Base

Common settings for Go jobs, including caching and private module access helpers. Extend these jobs to keep Go toolchain configuration consistent across pipelines.

### Usage

```yaml
include:
  - component: gitlab.com/shortlink-org/gitlab-templates/go@<version>

lint:
  extends:
    - .go-cache
    - .job_teplate_go
  script:
    - go vet ./...
```

### Inputs

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `stage` | string | `test` | Stage for `.job_teplate_go`. |
| `go_path` | string | `$CI_PROJECT_DIR/.go` | GOPATH used for caching modules. |

### Provided snippets

- `.go-cache` — configures module cache under `.go/pkg/mod`.
- `.job_teplate_go` — sets the Go image, stage, and interruptible behavior.
- `.go-private-repository` — pre-authenticates GitLab-hosted private modules via `CI_JOB_TOKEN`.

### Notes

- The base image tracks `golang:1.25-alpine`. Update when bumping Go toolchains.
- Combine with project-specific jobs (tests, linting) by extending the provided templates.

