# polyrepo-actions-hub

Public GitHub Actions hub for building and deploying multiple private repositories.

## What this repo does

- Keeps CI/CD orchestration in one public repository.
- Pulls private repositories during GitHub Actions runs with a repository access token.
- Builds one target repository or all enabled repositories from `config/repositories.json`.
- Lets each repository define its own build commands.

## Required secret

Create a repository secret named `CI_REPO_TOKEN`.

Recommended token:

- Fine-grained personal access token.
- Repository access: only the private repositories this hub needs to build.
- Permissions: `Contents: Read` is enough for checkout-only CI. Add only the deployment permissions your release process actually needs.

## Configure repositories

Edit `config/repositories.json`:

```json
{
  "repositories": [
    {
      "name": "service-a",
      "repository": "yongxin100/PRIVATE_REPO_A",
      "default_ref": "main",
      "workdir": ".",
      "build": [
        "go version",
        "go test ./..."
      ],
      "enabled": true
    }
  ]
}
```

Fields:

- `name`: short target name used by the workflow input.
- `repository`: GitHub repository in `owner/name` format.
- `default_ref`: branch, tag, or commit used when the workflow input `ref` is empty.
- `workdir`: directory inside the checked-out repository where commands should run.
- `build`: ordered shell commands.
- `enabled`: disabled entries are ignored.

## Run manually

Open **Actions** -> **Multi-repo CI/CD** -> **Run workflow**.

Inputs:

- `target`: `all` or a configured repository `name`.
- `ref`: optional branch, tag, or commit override.
- `deploy`: set to `true` to run the placeholder deploy job.

## Notes

This repository is public by design. Do not commit private repository names, internal URLs, environment values, or deploy credentials unless they are safe to expose publicly. Keep sensitive values in GitHub Actions secrets or environment secrets.
