# Setup

## 1. Create the repository

Recommended repository:

- Owner: `huangpj0210`
- Name: `polyrepo-actions-hub`
- Visibility: Public

## 2. Add secret

Add project-specific secrets and variables in:

`Settings` -> `Secrets and variables` -> `Actions` -> `New repository secret`

## 3. Add project workflows

Add one workflow file per project under `.github/workflows/`.

Keep private repository URLs, token values, registry hosts, and deploy targets in secrets instead of workflow files.

## 4. Run

Use the manual workflow dispatch first. After a project workflow works, add scheduled runs or repository dispatch triggers as needed.
