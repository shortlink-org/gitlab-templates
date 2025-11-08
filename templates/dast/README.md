## DAST Template

Use this component to add GitLab Dynamic Application Security Testing (DAST) into your pipelines with typed inputs for target URLs, authentication, and scan behaviour. It wraps the upstream `Security/DAST.gitlab-ci.yml` template so you can control the scan through pipeline inputs instead of ad-hoc variables.

### Usage

```yaml
include:
  - component: gitlab.com/shortlink-org/gitlab-templates/dast@<version>
    inputs:
      target_url: "https://staging.example.com"
      full_scan: false
      auth_url: "https://staging.example.com/login"
      auth_username: "$DAST_USERNAME"
      auth_password: "$DAST_PASSWORD"
```

### Inputs

- `target_url` (**required**) — URL of the application under test. The pipeline rule prevents the job from running when this value is empty.
- `full_scan` — toggle active scanning (`true`) versus faster passive-only scanning (`false`). Defaults to `false`.
- `auth_*` fields — configure optional browser-based authentication for protected environments. Leave blank for unauthenticated scans.
- `extra_headers` — pass additional HTTP headers such as feature flags or custom auth tokens.
- `allow_failure` — permit the pipeline to continue even if the scan detects high-severity findings.

### Documentation

- [Guide: A comprehensive guide to GitLab DAST](https://about.gitlab.com/blog/comprehensive-guide-to-gitlab-dast/)

