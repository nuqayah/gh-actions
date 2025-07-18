# GitHub Actions

## Example

```yaml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    uses: nuqayah/gh-actions/.github/workflows/deploy.yaml@main
    secrets:
      SSH_PRIVATE_KEY: ${{ secrets.SSH_PRIVATE_KEY }}
      DEPLOY_HOST: ${{ secrets.DEPLOY_HOST }}
      DEPLOY_USER: ${{ secrets.DEPLOY_USER }}
```

## Set Secrets
```bash
gh secret set SSH_PRIVATE_KEY < gh-key
gh secret set DEPLOY_HOST -b ...
gh secret set DEPLOY_USER -b ...
```
