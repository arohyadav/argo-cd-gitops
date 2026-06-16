# 🚀 Argo CD GitOps Repository

<p align="center">
  <img src="https://img.shields.io/badge/GitOps-ArgoCD-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Helm-Charts-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Argo-Rollouts-orange?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Kubernetes-Multi--Environment-326CE5?style=for-the-badge" />
</p>

## 📖 Overview

This repository follows the **GitOps** approach to manage Kubernetes deployments across multiple environments using **Argo CD**, **Helm**, and **Argo Rollouts**.

Every change pushed to Git is automatically synchronized with the Kubernetes clusters, ensuring deployments remain declarative, consistent, and version-controlled.

---

## ✨ Tech Stack

| Tool             | Purpose                                    |
| ---------------- | ------------------------------------------ |
| 🚀 Argo CD       | Continuous Delivery & GitOps               |
| 📦 Helm          | Kubernetes Package Management              |
| 🔄 Argo Rollouts | Progressive Delivery (Canary / Blue-Green) |
| ☸️ Kubernetes    | Container Orchestration                    |

---

## 🌍 Environments

| Environment   | Purpose                          |
| ------------- | -------------------------------- |
| 🧪 QA         | Initial testing and validation   |
| 🚦 Staging    | Pre-production verification      |
| 🚀 Production | Live customer-facing environment |

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
│   ├── helm-values/
│   │   ├── qa-values.yaml
│   │   ├── staging-values.yaml
│   │   └── prod-values.yaml
│   │
│   ├── qa/
│   ├── staging/
│   └── prod/
│
└── README.md
```

---

# ⚙️ Deployment Workflow

```text
Developer
     │
     ▼
 Push to GitHub
     │
     ▼
 Argo CD detects changes
     │
     ▼
 Sync Kubernetes manifests
     │
     ▼
 Deploy Helm Charts
     │
     ▼
 Argo Rollouts
 (Canary / Blue-Green)
     │
     ▼
 Kubernetes Cluster
```

---

# 🚀 Features

* ✅ GitOps-based Kubernetes deployments
* ✅ Multi-environment support (QA, Staging, Production)
* ✅ Environment-specific Helm values
* ✅ Automated synchronization using Argo CD
* ✅ Progressive delivery with Argo Rollouts
* ✅ Reusable Helm charts
* ✅ Declarative infrastructure stored in Git
* ✅ Easy rollback using Git history

---

# 📁 Environment Configuration

Each environment maintains its own Kubernetes manifests and Helm values.

```text
kubernetes/
├── qa/
├── staging/
├── prod/
└── helm-values/
```

This separation allows every environment to have independent configuration while sharing common deployment logic.

---

# 🚀 Getting Started

### 1. Install Argo CD

Install Argo CD into your Kubernetes cluster.

### 2. Apply ApplicationSets

```bash
kubectl apply -f applicationset/
```

### 3. Verify Applications

```bash
argocd app list
```

### 4. Sync Applications

```bash
argocd app sync <application-name>
```

---

# 🔄 Deployment Strategy

This repository supports **Argo Rollouts** for safer deployments.

Supported strategies include:

* Canary Deployments
* Blue-Green Deployments
* Automated Promotion
* Manual Promotion
* Rollback Support

---

# 📦 Helm

Environment-specific Helm values are stored under:

```text
kubernetes/helm-values/
```

Example:

```text
helm-values/
├── qa-values.yaml
├── staging-values.yaml
└── prod-values.yaml
```

This enables deploying the same chart with different configurations for each environment.

---

# 📌 Best Practices

* Keep environment-specific configuration isolated.
* Review pull requests before merging.
* Use Argo CD auto-sync where appropriate.
* Store secrets securely (External Secrets, Vault, Sealed Secrets, etc.).
* Keep Helm values minimal and reusable.
* Prefer declarative changes over manual cluster modifications.

---

# 📈 GitOps Flow

```text
Git Commit
     │
     ▼
GitHub Repository
     │
     ▼
Argo CD Watches Repository
     │
     ▼
Synchronizes Desired State
     │
     ▼
Kubernetes Cluster
```

---

# 📚 References

* Argo CD
* Argo Rollouts
* Helm
* Kubernetes

---

## 👨‍💻 Author

**Aroh Yadav**

DevOps • Kubernetes • GitOps • Cloud Infrastructure

---

## 📄 License

This project is licensed under the MIT License.
