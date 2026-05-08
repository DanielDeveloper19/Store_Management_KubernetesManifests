# ☸️ Store Management: GitOps Manifests
> **The Source of Truth for Production State.**

This repository acts as the **Declarative State** for the Store Management application. By utilizing a **GitOps Pull-Model**, this repo ensures that the production environment on AWS EKS always matches the configuration defined here.

## 📦 Deployment Strategy: Helm
We utilize **Helm Charts** to manage application complexity and environment-specific configurations.
* **Standardized Templates:** Unified Deployment, Service, and Ingress resources.
* **Dynamic Tagging:** The CI pipeline automatically updates the `image.tag` in `values.yaml` to trigger seamless rollouts.
* **Secret Management:** Secure injection of RDS credentials and environment variables.

## 🐙 GitOps with ArgoCD
This repository is continuously monitored by **ArgoCD**.
* **Auto-Sync:** Changes pushed to the `HEAD` of this repo are instantly reconciled in the EKS cluster.
* **Self-Healing:** Any manual changes (drifts) made to the cluster are automatically overwritten to match this Git source of truth.
* **Observability:** Integrated with **Prometheus and Grafana** for real-time monitoring of pod health and resource utilization.

## 🚀 Deployment
This application is part of a larger GitOps ecosystem. It is automatically deployed to an **AWS EKS** cluster whenever the `master` branch is updated.
* **Orchestration:** https://github.com/DanielDeveloper19/Store_Management_Terraform_EKS_kubernetes_infra_AWS.git
* | **💻 Business Logic** | Java Spring Boot Application | [Source Code Repo](https://github.com/DanielDeveloper19/store_management.git) 

## 📂 Repository Structure
```text
.
├── storeManagement_chart/          # Main Application Helm Chart
│   ├── templates/                  # K8s Resource Templates (Deployment, Service, Ingress)
│   ├── values.yaml                 # Default production configurations
│   └── Chart.yaml                  # Metadata and versioning
└── README.md
