# GitHub Actions

## Reusable Deploy Workflow

A reusable workflow for deploying applications to a server via SSH.

### Usage

```yaml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    uses: nuqayah/gh-actions/.github/workflows/deploy.yml@main
    with:
      app_name: your-app
      # Optional parameters
      service_name: your-service           # Defaults to app_name
      deploy_backend: true                 # Whether to deploy backend code
      backend_setup_command: "npm install" # Command to run after backend deployment
      frontend_dist_path: "dist"           # Path to frontend build files
      frontend_target_path: "public"       # Target path on server
    secrets:
      SSH_PRIVATE_KEY: ${{ secrets.SSH_PRIVATE_KEY }}
      DEPLOY_HOST: ${{ secrets.DEPLOY_HOST }}
      DEPLOY_USER: ${{ secrets.DEPLOY_USER }}
```

### Parameters

| Input | Required | Default | Description |
|-------|----------|---------|-------------|
| `app_name` | Yes | - | Application name used for deployment path |
| `service_name` | No | `app_name` | Service name to restart |
| `deploy_backend` | No | `false` | Whether to deploy the backend |
| `backend_setup_command` | No | `mise x -- uv sync --inexact` | Command to run after backend deployment |
| `frontend_dist_path` | No | `dist/index.html` | Path to frontend build files |
| `frontend_target_path` | No | `src` | Target path for frontend files on server |

### Set Secrets
```bash
gh secret set SSH_PRIVATE_KEY -b ...
gh secret set DEPLOY_HOST -b ...
gh secret set DEPLOY_USER -b ...
```
