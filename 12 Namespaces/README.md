# Kubernetes - Namespaces

This section covers **Namespaces** in Kubernetes, which are used to organize and isolate resources within a cluster.

---

## 🧠 Key Concepts

- **Namespaces** allow segmentation of resources (Pods, Services, Deployments, etc.) within the same cluster.
- Useful for:
  - Multi-team environments
  - Environment separation (dev, staging, prod)
  - Access control (via RBAC)
- The default namespaces include:
  - `default`
  - `kube-system`
  - `kube-public`
  - `kube-node-lease`

---

## ✅ Usage

### 🏷️ List All Namespaces
```bash
kubectl get namespaces
```

### ➕ Create a Namespace
```bash
kubectl create namespace <namespace-name>
```

### 🔁 Use a Namespace Temporarily
```bash
kubectl get pods --namespace=<namespace-name>
```

### 🔁 Set a Default Namespace for Context
```bash
kubectl config set-context --current --namespace=<namespace-name>
```

### ❌ Delete a Namespace
```bash
kubectl delete namespace <namespace-name>
```

---

## 🔧 Deploy Resources to a Namespace

Specify namespace in manifest:
```yaml
metadata:
  name: my-pod
  namespace: my-namespace
```

Or use `-n` flag when applying:
```bash
kubectl apply -f app.yaml -n my-namespace
```

---

## 📌 Notes

- Namespaces do **not** provide network isolation by default.
- Use **NetworkPolicies** to restrict traffic between namespaces.
- Resource quotas and limits can be scoped per namespace.

---

🧠 Practice organizing your deployments into different namespaces and monitor their scoped behavior using `kubectl`.

