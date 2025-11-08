## Markdown Link Checker

Scans Markdown files for broken links using `markdown-link-check`. Useful for documentation repositories or monorepos with extensive docs coverage.

### Usage

```yaml
include:
  - component: gitlab.com/shortlink-org/gitlab-templates/linkchecker@<version>
    inputs:
      stage: test
      allow_failure: true
```

### Inputs

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `stage` | string | `test` | Stage for the link checking job. |
| `allow_failure` | boolean | `true` | Whether broken links fail the pipeline. |
| `tags` | array | `["gitlab-org-docker"]` | Runner tags to target when executing the job. |

### Notes

- Job triggers automatically on Markdown changes (`rules:changes`) and on tags.
- The container image runs link checking via `find` + `markdown-link-check`. Adjust the script if you need different ignore patterns.

