# polyrepo-actions-hub

Public GitHub Actions hub for building and deploying multiple private repositories.

## What this repo does

- Keeps CI/CD orchestration in one public repository.
- Uses one workflow file per project.
- Keeps private source repository URLs and deployment credentials in GitHub Actions secrets.
- Lets the source repository Dockerfile build the application binary and final image.

## device-metrics

Workflow:

`.github/workflows/device-metrics.yml`

## Run manually

Open **Actions** -> **device-metrics** -> **Run workflow**.

Inputs:

- `branch`: source branch to build, picked from a dropdown.
- `deploy`: set to `true` to build and push a Docker image. It defaults to `true`.
- `image_tag`: optional Docker image tag. If empty, the workflow uses the source repository commit SHA prefix.

## Container registry

Images are pushed to Tencent Cloud Container Registry (TCR personal edition). The registry host is `ccr.ccs.tencentyun.com` (`hkccr.ccs.tencentyun.com` for Hong Kong).

TCR puts the namespace inside the repository path. The namespace (`chicony`) and the repository name (`device-metrics`) are fixed in the workflow's job-level `env`, so any new workflow only needs to copy those two lines and change the repository name.

```
ccr.ccs.tencentyun.com/chicony/device-metrics:<tag>
```

## Configuration

| Name | Kind | Value |
| --- | --- | --- |
| `DOCKER_REGISTRY_HOST` | Variable | `ccr.ccs.tencentyun.com` |
| `DOCKER_REGISTRY_USERNAME` | Secret | TCR login user (Tencent Cloud account ID) |
| `DOCKER_REGISTRY_PASSWORD` | Secret | TCR login password |
| `DEVICE_METRICS_GIT_URL` | Secret | Private source repository URL |
| `DEVICE_METRICS_REPO_SSH_KEY` | Secret | Only for `git@` / `ssh://` source URLs |
| `GH_USERNAME` / `GH_TOKEN` | Secret | Only for `https://github.com/` source URLs |

## Notes

This repository is public by design. Keep source URLs, registry settings, and credentials in GitHub Actions variables or secrets.
