# argo-cd-gitops

## Overview

This repository implements GitOps deployment for a multi-environment Kubernetes application using:

- **Argo CD** for managing application manifests and Helm chart deployments.
- **Argo Rollouts** for progressive delivery and advanced deployment strategies.
- **Helm** to package and manage reusable Kubernetes resources.

The deployment pipeline targets three environments:

- `qa`
- `staging`
- `prod`

## Repository Structure

- `applicationset/`
  - Argo CD Application definitions for QA, staging, and production.
  - Helm chart application manifest for `kube-prometheus-stack`.
  - Shared secret management manifest.
- `kubernetes/`
  - `helm-values/` stores environment-specific Helm values.
  - `prod/`, `staging/`, `qa/` folders store environment-specific Kubernetes manifests.

## How It Works

1. Git changes are pushed to this repository.
2. Argo CD syncs the repository state to Kubernetes clusters for each environment.
3. Helm charts are deployed and managed through Argo CD application manifests.
4. Argo Rollouts handles rollout strategies like canary, blue-green, and automated promotion.

## Environments

### QA

- Used for initial validation and testing.
- Contains application manifests and environment-specific configuration.

### Staging

- Mirrors production as closely as possible.
- Used for release validation before production promotion.

### Production

- Runs the live, customer-facing version of the application.
- Receives validated changes after QA and staging approvals.

## Key Features

- GitOps-managed deployments across QA, staging, and production.
- Argo CD for declarative application delivery.
- Helm chart values managed in repository for consistent configuration.
- Support for progressive delivery using Argo Rollouts.

## Usage

1. Install and configure Argo CD in your cluster.
2. Create Argo CD Applications or ApplicationSets that target this repository.
3. Apply the manifests under `applicationset/` to register QA, staging, and production applications.
4. Update Helm values or Kubernetes manifests in `kubernetes/` to deploy changes.

## Notes

- Keep environment-specific values in `kubernetes/<env>/` and `kubernetes/helm-values/`.
- Use branch-based or folder-based GitOps patterns depending on your release workflow.
- Argo Rollouts manifests should be added or updated for each service requiring progressive deployment.

## License

This repository is provided as-is. Update the license section to match your project requirements.
