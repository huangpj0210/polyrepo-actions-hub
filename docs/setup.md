# Setup

## 1. Create the repository

Recommended repository:

- Owner: `huangpj0210`
- Name: `polyrepo-actions-hub`
- Visibility: Public

## 2. Add secret

Add `CI_REPO_TOKEN` in:

`Settings` -> `Secrets and variables` -> `Actions` -> `New repository secret`

The token must be able to read every private `yongxin100` repository listed in `config/repositories.json`.

## 3. Add repositories

Add one entry per repository in `config/repositories.json`.

Keep entries disabled until their build commands are verified:

```json
"enabled": false
```

## 4. Run

Use the manual workflow dispatch first. After the matrix works, add scheduled runs or repository dispatch triggers as needed.
