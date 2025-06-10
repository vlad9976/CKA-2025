# Kubernetes - Helm Basics

This section introduces **Helm**, the package manager for Kubernetes.  
Helm simplifies application deployment and management by using templated charts.

---

## 🧠 Key Concepts

- A **Chart** is a Helm package that contains:
  - `Chart.yaml` (metadata)
  - `values.yaml` (default configuration)
  - Templates (`templates/*.yaml`)
- Helm helps:
  - Install and upgrade apps easily
  - Reuse common deployment patterns
  - Centralize configuration

---

## ✅ Helm Commands

### 📦 Install a Chart
```bash
helm install <release-name> <chart-path-or-repo>
```

### 🔁 Upgrade a Release
```bash
helm upgrade <release-name> <chart-path-or-repo>
```

### ❌ Uninstall a Release
```bash
helm uninstall <release-name>
```

### 🔍 List Installed Releases
```bash
helm list
```

### 🎯 Template Rendering (preview manifests)
```bash
helm template <release-name> <chart-path>
```

---

## 🧰 Chart Structure Example

```
mychart/
├── Chart.yaml
├── values.yaml
├── charts/
├── templates/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── _helpers.tpl
```

---

## 📚 Helpful Resources

- Helm Docs: https://helm.sh/docs/
- Artifact Hub (for finding charts): https://artifacthub.io/

---

🧠 Practice creating your own charts and templating reusable resources like Deployments and Services!
