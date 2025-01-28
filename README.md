# GitOps Repository

This repository manages the **GitOps workflow** for deploying applications to different environments using **ArgoCD**. Each environment (`dev`, `test`, `prod`) is represented by a separate directory with configuration files that define the deployment settings and application resources.

---

## How It Works

1. **ArgoCD as a Continuous Delivery Tool**:
   - This repository is integrated with **ArgoCD**, which continuously monitors changes in this repository to update the state of Kubernetes clusters.
   - Each environment is managed via an **ArgoCD Application resource** that defines:
     - The Git repository and branch to track (corresponding to the Application repository).
     - The Helm chart and `values.yaml` file to use for deployment.

2. **Environment-Specific Configurations**:
   - Each environment (`dev`, `test`, `prod`) "listens" to a different branch in the **Application Repository**.
   - Updates to the respective branch in the Application Repository trigger changes in the environment through ArgoCD.

---

## Directory Structure
```plaintext
.
└── environments
    ├── dev
    │   ├── application.yaml
    │   └── values.yaml
    ├── prod
    │   ├── application.yml
    │   └── values.yml
    └── test
        ├── application.yml
        └── values.yml
```
## Key Features

1. **Environment-Specific Deployments**:
   - Each environment (`dev`, `test`, `prod`) is configured separately.
   - Environments are mapped to specific branches in the **Application Repository**:
     - `dev` listens to the `dev` branch.
     - `test` listens to the `test` branch.
     - `prod` listens to the `main` or `prod` branch.

2. **ArgoCD Application Resource**:
   - Each `application.yaml` file defines an ArgoCD `Application` resource, specifying:
     - The Git repository and branch to monitor.
     - The Helm chart to use for deployment.
     - The values reference for each environment.
     - Sync policies to automate deployment.
