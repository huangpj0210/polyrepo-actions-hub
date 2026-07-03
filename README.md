# polyrepo-actions-hub

Public GitHub Actions hub for building and deploying multiple private repositories.

## What this repo does

- Keeps CI/CD orchestration in one public repository.
- Uses one workflow file per project.
- Keeps private source repository URLs and deployment credentials in GitHub Actions secrets.
- Lets the source repository Dockerfile build the application binary and final image.

## miniapi

Workflow:

`.github/workflows/miniapi.yml`

## im-callback-http

Workflow:

`.github/workflows/im-callback-http.yml`

## Run manually

Open **Actions** -> **miniapi CI/CD** -> **Run workflow**.

Inputs:

- `ref`: optional branch, tag, or commit override.
- `deploy`: set to `true` to build and push a Docker image. It defaults to `true`.
- `image_tag`: optional Docker image tag. If empty, the workflow uses the source repository commit SHA prefix.

## Notes

This repository is public by design. Keep source URLs, registry settings, and credentials in GitHub Actions variables or secrets.
