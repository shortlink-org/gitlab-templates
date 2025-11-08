## Code Intelligence (Go)

Generate an LSIF index for Go repositories using Sourcegraph’s `scip-go` image. The job is manual by default so you can run it on demand when you need fresh code navigation data.

### Usage

```yaml
include:
  - component: gitlab.com/shortlink-org/gitlab-templates/code_intelligence@<version>
    inputs:
      stage: .pre
```

### Inputs

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `stage` | string | `.pre` | Pipeline stage where the LSIF job runs. |
| `allow_failure` | boolean | `true` | Whether a failing LSIF job fails the pipeline. |
| `artifacts_expire_in` | string | `14 days` | Retention for the generated `dump.lsif` artifact. |

### Notes

- The job uses `lsif-go` to produce a SCIP bundle and stores it as an LSIF artifact.
- Keep the job manual unless you want code intelligence on every pipeline, because indexing may take a long time on large projects.

