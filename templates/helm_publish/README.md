## Helm Chart Publish

Package a chart and upload it to the GitLab Helm registry. Builds on the Helm base component for plugin and SOPS support.

### Usage

```yaml
include:
  - component: gitlab.com/shortlink-org/gitlab-templates/helm_publish@<version>

variables:
  HELM_CHART_PATH: charts/my-app
  HELM_CHART_NAME: my-app
```

### Notes

- `helm-chart` job packages the chart, extracts the version with `yq`, and uploads it using `curl` against the project’s Helm endpoint.
- Requires the project to define `HELM_CHART_PATH` and `HELM_CHART_NAME` variables (either in `.gitlab-ci.yml` or CI/CD settings).
- Include the `common` component to inherit shared Docker settings if needed.

