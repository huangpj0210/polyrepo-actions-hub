# Setup

## 1. Create the repository

Recommended repository:

- Owner: `huangpj0210`
- Name: `polyrepo-actions-hub`
- Visibility: Public

## 2. Add secrets

Add repository secrets in:

`Settings` -> `Secrets and variables` -> `Actions`

The image namespace and repository name are fixed in `.github/workflows/device-metrics.yml` (`REGISTRY_NAMESPACE: chicony`, `IMAGE_NAME: device-metrics`), not in repository settings.

Secrets:

- `DOCKER_REGISTRY_HOST` = `ccr.ccs.tencentyun.com`
- `DOCKER_REGISTRY_USERNAME` = `100005971004`
- `DOCKER_REGISTRY_PASSWORD` (TCR login password, filled in manually)
- `DEVICE_METRICS_GIT_URL`
- `DEVICE_METRICS_REPO_SSH_KEY` (SSH source URL) or `GH_USERNAME` + `GH_TOKEN` (HTTPS source URL)

## 3. Add project workflows

Add one workflow file per project under `.github/workflows/`.

Keep private repository URLs, token values, registry hosts, and deploy targets in variables or secrets instead of workflow files.

## 4. Run

Use the manual workflow dispatch first. After a project workflow works, add scheduled runs or repository dispatch triggers as needed.
