# GitLab CI Templates

## Docs

- [Documentation: CI/CD components overview](https://docs.gitlab.com/ci/components/)
- [Tutorial: How to set up your first GitLab CI/CD component](https://about.gitlab.com/blog/2024/11/12/tutorial-how-to-set-up-your-first-gitlab-ci-cd-component/)
- [Blog: Migrate from pipeline variables to pipeline inputs for better security](https://about.gitlab.com/blog/migrate-from-pipeline-variables-to-pipeline-inputs-for-better-security/)

## Components

### Foundations

- [Common defaults](templates/common/README.md)
- [pnpm cache](templates/pnpm_cache/README.md)

### Build & Release

- [Docker build](templates/docker_build/README.md)
- [Docker pipeline](templates/docker_pipeline/README.md)
- [Helm base](templates/helm/README.md)
- [Helm publish](templates/helm_publish/README.md)
- [npm publish](templates/npm_publish/README.md)

### Deploy & Ops

- [CRD apply](templates/crd/README.md)
- [Helm deploy](templates/helm_deploy/README.md)

### Testing & Quality

- [Code intelligence (Go)](templates/code_intelligence/README.md)
- [Go base](templates/go/README.md)
- [Go test](templates/gotest/README.md)
- [Markdown link checker](templates/linkchecker/README.md)
- [DAST](templates/dast/README.md)

### Security & Maintenance

- [Dependabot flow](templates/dependabot-flow/README.md)
