# polyrepo-actions-hub

Public GitHub Actions hub for building and deploying multiple private repositories.

## What this repo does

- Keeps CI/CD orchestration in one public repository.
- Uses one workflow file per project.
- Keeps private source repository URLs and deployment credentials in GitHub Actions secrets.
- Pulls private Gitee or GitHub repositories during Actions runs.

## quxin-miniapi

Workflow:

`.github/workflows/quxin-miniapi.yml`

Required secrets:

- `GITEE_USERNAME`: Gitee username that owns the token.
- `GITEE_TOKEN`: Gitee personal access token with read access to the source repository.
- `QUXIN_MINIAPI_GIT_URL`: private Gitee HTTPS URL.

Do not include the token in `QUXIN_MINIAPI_GIT_URL`. Keep it as a plain HTTPS repository URL; the workflow injects the token at runtime using Gitee's `https://<user>:<token>@gitee.com/<owner>/<repo>.git` format.

Optional deploy secrets:

- `QX_REGISTRY_HOST`: container registry host.
- `QX_REGISTRY_USERNAME`: container registry username.
- `QX_REGISTRY_PASSWORD`: container registry password.
- `QX_MINIAPI_IMAGE_NAME`: private image repository name.

Project-specific sensitive values should be injected with additional GitHub Actions secrets. Avoid baking runtime passwords or production config into Docker images; prefer passing those values through your deployment platform.

## Run manually

Open **Actions** -> **quxin-miniapi CI/CD** -> **Run workflow**.

Inputs:

- `ref`: optional branch, tag, or commit override.
- `deploy`: set to `true` to build and push a Docker image.
- `image_tag`: optional Docker image tag. If empty, the workflow uses the GitHub Actions commit SHA prefix.

## Notes

This repository is public by design. Do not commit private repository URLs, internal service addresses, environment values, registry credentials, or deploy credentials. Keep sensitive values in GitHub Actions secrets or environment secrets.
