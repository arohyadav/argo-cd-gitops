# 🚀 Argo CD GitOps Repository

<p align="center">
  <img src="https://img.shields.io/badge/GitOps-ArgoCD-red?style=for-the-badge">
  <img src="https://img.shields.io/badge/Helm-Charts-blue?style=for-the-badge">
  <img src="https://img.shields.io/badge/Argo-Rollouts-orange?style=for-the-badge">
  <img src="https://img.shields.io/badge/Kubernetes-Multi--Environment-326CE5?style=for-the-badge">
</p>

A GitOps repository for managing Kubernetes deployments across **QA**, **Staging**, and **Production** using **Argo CD**, **Helm**, and **Argo Rollouts**.

---
                    GitHub
                       │
             Git Push / Pull Request
                       │
                       ▼
                 Argo CD Watches Repo
                       │
         ┌─────────────┴─────────────┐
         │             │             │
         ▼             ▼             ▼
       QA Cluster   Staging      Production
         │             │             │
         └────── Argo Rollouts ──────┘
                    │
               Helm Charts
                    │
             Kubernetes Resources

# 📖 Overview

This repository follows the GitOps model where **Git is the single source of truth** for Kubernetes deployments.

It manages:

* Kubernetes manifests
* Helm chart deployments
* Environment-specific configurations
* Progressive delivery using Argo Rollouts

Whenever changes are pushed to this repository, **Argo CD** automatically synchronizes the desired state with the Kubernetes cluster.

---

# 🛠 Tech Stack

| Component        | Purpose                         |
| ---------------- | ------------------------------- |
| ☸️ Kubernetes    | Container orchestration         |
| 🚀 Argo CD       | GitOps Continuous Delivery      |
| 📦 Helm          | Package management              |
| 🔄 Argo Rollouts | Canary & Blue-Green deployments |

---

# 🌍 Deployment Environments

| Environment   | Description                    |
| ------------- | ------------------------------ |
| 🧪 QA         | Initial testing and validation |
| 🚦 Staging    | Pre-production verification    |
| 🚀 Production | Live production workloads      |

---

# 📂 Repository Structure

```text
argo-cd-gitops/
│
├── applicationset/
│   ├── qa.yaml
│   ├── staging.yaml
│   ├── prod.yaml
│   ├── kube-prometheus-stack.yaml
│   └── shared-secrets.yaml
│
├── kubernetes/
│   ├── qa/
│   ├── staging/
│   ├── prod/
│   └── helm-values/
│       ├── qa-values.yaml
│       ├── staging-values.yaml
│       └── prod-values.yaml
│
└── README.md
```

---

# ⚙️ Deployment Workflow

```text
Developer
     │
     ▼
Push Changes to GitHub
     │
     ▼
Argo CD Detects Changes
     │
     ▼
Synchronizes Kubernetes Resources
     │
     ▼
Deploys Helm Charts
     │
     ▼
Argo Rollouts
(Canary / Blue-Green)
     │
     ▼
Kubernetes Cluster
```

---

# ✨ Features

* GitOps-driven deployments
* Multi-environment support
* Environment-specific Helm values
* Declarative Kubernetes manifests
* Progressive delivery using Argo Rollouts
* Automated synchronization with Argo CD
* Easy rollback using Git history

---

# 🚀 Getting Started

## 1. Install Argo CD

Install Argo CD in your Kubernetes cluster.

## 2. Register Applications

```bash
kubectl apply -f applicationset/
```

## 3. Verify

```bash
argocd app list
```

## 4. Sync Applications

```bash
argocd app sync <application-name>
```

---

# 📌 Best Practices

* Store environment-specific configuration separately.
* Keep Helm charts reusable.
* Review Pull Requests before merging.
* Avoid manual cluster changes.
* Use Git commits as the deployment history.

---

# 📄 License

This project is licensed under the MIT License.
