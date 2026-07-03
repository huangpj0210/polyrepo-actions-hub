# Setup

## 1. Create the repository

Recommended repository:

- Owner: `huangpj0210`
- Name: `polyrepo-actions-hub`
- Visibility: Public

## 2. Add secret

Add required source checkout secrets in:

`Settings` -> `Secrets and variables` -> `Actions` -> `New repository secret`

- `GITEE_USERNAME`: Gitee username that owns the token.
- `GITEE_TOKEN`: Gitee personal access token with read access to the private Gitee repository.
- `QUXIN_MINIAPI_GIT_URL`: private Gitee HTTPS URL.

Do not include the token in `QUXIN_MINIAPI_GIT_URL`. Keep it as a plain HTTPS repository URL.

For Docker image publishing, add:

- `QX_REGISTRY_HOST`
- `QX_REGISTRY_USERNAME`
- `QX_REGISTRY_PASSWORD`
- `QX_MINIAPI_IMAGE_NAME`

## 3. Add project workflows

Add one workflow file per project under `.github/workflows/`.

Keep private repository URLs, token values, registry hosts, and deploy targets in secrets instead of workflow files.

## 4. Run

Use the manual workflow dispatch first. After a project workflow works, add scheduled runs or repository dispatch triggers as needed.
