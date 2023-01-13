# Learning [action-dependabot-auto-merge](https://github.com/ahmadnassri/action-dependabot-auto-merge)

Just one of the things I'm learning. https://github.com/hchiam/learning

## At least once

Set up a [PAT (Personal Access Token)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) named `mytoken` with these scopes:

- `repo` for private repositories
- `public_repo` for public repositories

## Per repo

Go to: **Settings** > **Security** > **Secrets and variables** > **Dependabot** > **New repository secret** > **Name:** mytoken, **Secret:** (paste PAT) > **Add secret**

Create this file:

```txt
.github/workflows/dependabot_auto_merge.yml
```

Literally post this into that file: (yes, literally `${{ secrets.mytoken }}`)

```yml
name: dependabot_auto_merge

on:
  pull_request:

jobs:
  auto-merge:
    runs-on: ubuntu-latest
    steps:
      - uses: ahmadnassri/action-dependabot-auto-merge@v2
        with:
          github-token: ${{ secrets.mytoken }}
```
