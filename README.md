# Helm for DevOps: Self-Practices Workspace ⛵

Welcome to the **Helm Self-Practices Workspace**. This repository is dedicated to mastering Helm, the package manager for Kubernetes. It serves as a personal sandbox for creating, linting, packaging, and deploying Helm charts, ranging from simple web applications to complex multi-tier microservices.

---

## 🏗️ Workspace Structure

```text
.
├── README.md
├── charts/                      # Directory for your custom Helm charts
│   └── my-demo-app/             # Example practice chart
│       ├── Chart.yaml           # Metadata about the chart
│       ├── values.yaml          # Default configuration values
│       ├── templates/           # Kubernetes manifest templates
│       │   ├── deployment.yaml
│       │   ├── service.yaml
│       │   └── _helpers.tpl     # Named templates/helpers
│       └── charts/              # Sub-charts (dependencies)
└── environments/                # Practice environment-specific value overrides
    ├── dev-values.yaml
    └── prod-values.yaml

```

---

## 🧠 Core Architecture Concepts

Helm simplifies Kubernetes deployments by managing three vital pieces:

1. **The Chart**: Your blueprint of Kubernetes resources (Deployments, Services, Ingress, etc.).
2. **The Values**: The configuration parameters that customize the blueprint.
3. **The Release**: A running instance of a chart combined with specific values inside a cluster.

---

## 🛠️ Essential Practice Commands

Use these commands within this workspace to practice day-to-day DevOps Helm workflows.

### 1. Creating and Validating Charts

* **Create a new chart scaffold:**

```bash
helm create charts/my-new-app

```

* **Lint your chart for syntax errors or best practices:**

```bash
helm lint charts/my-demo-app

```

* **Dry-run & Template Rendering (See exactly what YAML will output without deploying):**

```bash
helm template my-release charts/my-demo-app --debug

```

### 2. Deploying and Managing Releases

* **Install a chart:**

```bash
helm install practice-release charts/my-demo-app

```

* **Install/Upgrade with environment-specific overrides:**

```bash
helm upgrade --install practice-release charts/my-demo-app -f environments/dev-values.yaml

```

* **List all active releases:**

```bash
helm list --all-namespaces

```

### 3. Rollbacks and History (The DevOps Superpower)

* **View release revision history:**

```bash
helm history practice-release

```

* **Rollback to a previous specific revision (e.g., Revision 1):**

```bash
helm rollback practice-release 1

```

* **Uninstall/Delete a release:**

```bash
helm uninstall practice-release

```

---

## 🧪 Active Exercises Checklist

* [ ] **Exercise 1:** Create a basic Nginx deployment chart and expose it via a `NodePort` service.
* [ ] **Exercise 2:** Use Dynamic Values (`{{ .Values.replicaCount }}`) to scale deployments up and down via `values.yaml`.
* [ ] **Exercise 3:** Practice using Named Templates (`_helpers.tpl`) to standardize resource labels.
* [ ] **Exercise 4:** Manage application secrets securely using Helm dry-runs combined with your favorite GitOps tools.

---

## 🎯 Tips for Success

* Always use `helm lint` before checking charts into Git.
* Keep production secrets out of `values.yaml` files (use environment variables, external secret managers, or `--set` flags during pipeline executions).
* Utilize `helm diff` (via the helm-diff plugin) in CI/CD pipelines to review structural changes before running deployments.

---
