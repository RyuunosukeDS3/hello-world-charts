# DevSecOps Hello World Charts

This repository contains Helm charts for the **Hello World frontend and backend** applications used in [DevSecOps Hello World GitOps](https://github.com/YOUR_USER/devsecops-hello-world-gitops).

Charts are built for use with **OCI registry support** and published as artifacts to GitHub Container Registry (GHCR).

---

## 🧭 Charts

- [`hello-world-frontend`](charts/hello-world-frontend/)
- [`hello-world-backend`](charts/hello-world-backend/)

Each chart includes:

- Kubernetes Deployments and Services
- Configurable Helm values
- Optional Ingress and PVC support
- Liveness/readiness probes

---

## 🚀 Publishing Charts to OCI (GitHub Container Registry)

Make sure you're logged in to GHCR:

```bash
helm registry login ghcr.io
````

To package and push a chart:

```bash
helm package charts/hello-world-backend
helm push hello-world-backend-*.tgz oci://ghcr.io/YOUR_USER/devsecops-hello-world-charts
```

Do the same for the frontend chart.

---

## 📦 Using the Charts

Sure! Here's a full step-by-step guide to **login, pull, and install** your OCI-based Helm chart from GitHub Container Registry (GHCR):

---

### ✅ 1. Log in to GitHub Container Registry (GHCR)

```bash
helm registry login ghcr.io
```

> You’ll be prompted for a username (your GitHub username) and a **Personal Access Token (PAT)** with at least the `read:packages` scope.
> You can generate one here: [https://github.com/settings/tokens](https://github.com/settings/tokens)

---

### ✅ 2. Install:

```bash
helm install hello-world-backend oci://ghcr.io/YOUR_USER/devsecops-hello-world-charts/hello-world-backend \
  --version 0.1.0 \
  --namespace hello \
  --create-namespace
```

---

### 🔄 3. Upgrade or Uninstall

Upgrade:

```bash
helm upgrade hello-world-backend oci://ghcr.io/YOUR_USER/devsecops-hello-world-charts/hello-world-backend \
  --version 0.1.1 \
  -n hello
```

Uninstall:

```bash
helm uninstall hello-world-backend -n hello
```

---

Would you like a GitHub Actions workflow to automate `helm package` + `helm push` on tag or PR?

## 📄 License

[MIT License](LICENSE)
