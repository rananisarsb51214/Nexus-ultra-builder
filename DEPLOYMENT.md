# DEPLOYMENT — Vercel / Docker / CI

Primary Platform: Vercel
Secondary: Docker
CI/CD: GitHub Actions

Overview

- Use Vercel for frontend and serverless API hosting. For self-hosted or private deployments use Docker images and orchestration (Kubernetes or docker-compose).
- CI pipeline should validate code quality, run tests, build preview, and only deploy on merge to main.

Secrets & Configuration

- Store secrets in GitHub Secrets for CI and Vercel Environment variables for runtime.
- Follow principle of least privilege for service accounts and tokens.
- Rotate credentials regularly and maintain rotation documentation.

Observability

- Emit structured logs and metrics. Integrate with a log/metrics provider (e.g., Datadog, Grafana, Sentry).
- Correlate requests with trace_id.

Rollback

- Use immutable builds and canary or preview deployments. In Vercel, use preview deployments for PRs and roll forward/rollback via promoted deployment.

CI example (GitHub Actions)

- name: CI
  on: [push, pull_request]
  jobs:
    lint:
      runs-on: ubuntu-latest
    test:
      runs-on: ubuntu-latest
    build:
      runs-on: ubuntu-latest

Deployment steps

1. Push branch → GitHub Actions runs CI → Preview deployed to Vercel
2. After approval: merge to main → Production deploy on Vercel

For Docker deployments

- Build multi-stage Dockerfile, scan image, push to registry, and deploy to target host/cluster.
