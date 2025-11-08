## Go Test

Runs Go tests with race detection, coverage reporting, and Cobertura/JUnit exports. Builds on the base Go templates to add tooling installation and artifacts.

### Usage

```yaml
include:
  - component: gitlab.com/shortlink-org/gitlab-templates/gotest@<version>
    inputs:
      stage: test
      allow_failure: false
```

### Inputs

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `stage` | string | `test` | Stage assigned to the `gotest` job. |
| `allow_failure` | boolean | `true` | Allow the test job to fail without failing the pipeline. |
| `coverage_pattern` | string | `/total:.*\d+.\d+%/` | Regex for parsing overall coverage from `go tool cover -func`. |
| `artifacts_expire_in` | string | `14 days` | Artifact retention for coverage reports. |

### Notes

- Installs `gocover-cobertura` and `gotestsum` to produce coverage and JUnit reports.
- Uses `go work vendor` prior to running tests; adjust if your project doesn’t rely on workspaces.
- Artifacts expose coverage results under “Code Coverage” in GitLab.

