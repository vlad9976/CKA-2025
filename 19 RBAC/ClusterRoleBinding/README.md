# Kubernetes - ClusterRole & ClusterRoleBinding

This section covers **ClusterRole** and **ClusterRoleBinding**, which are used to define and grant **cluster-wide permissions** in Kubernetes.

---

## 📁 File Overview

| File Name                 | Description                                |
|---------------------------|--------------------------------------------|
| 3cluster-role.yaml        | Defines a ClusterRole with global access   |
| 4Cluster-role-binding.yaml| Binds a user or service account globally   |

---

## 🧠 Key Concepts

- A **ClusterRole** defines a set of permissions **not limited to a single namespace**.
- A **ClusterRoleBinding** associates that role with a user, group, or service account across the whole cluster.
- Useful for:
  - Cluster-level operations (e.g., listing nodes)
  - Admin roles
  - Cross-namespace access

---

## ✅ Usage

### 1. Define a ClusterRole

Example from `3cluster-role.yaml`:
```yaml
kind: ClusterRole
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: cluster-reader
rules:
- apiGroups: [""]
  resources: ["pods", "nodes"]
  verbs: ["get", "list"]
```

Apply it:
```bash
kubectl apply -f 3cluster-role.yaml
```

---

### 2. Bind the ClusterRole Globally

Example from `4Cluster-role-binding.yaml`:
```yaml
kind: ClusterRoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: cluster-read-binding
subjects:
- kind: User
  name: dev-user
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: cluster-reader
  apiGroup: rbac.authorization.k8s.io
```

Apply it:
```bash
kubectl apply -f 4Cluster-role-binding.yaml
```

---

### 3. Verify Access

Use the bound user’s context and run:
```bash
kubectl get nodes
kubectl get pods --all-namespaces
```

---

## 📌 Notes

- ClusterRole can also be **bound to a namespace** using a RoleBinding (for advanced scoped access).
- Granting `*` verbs or all resources should be done cautiously and only to trusted users.
- Always audit bindings in production for least privilege access.

---

🧠 Practice by granting limited access to resources like `configmaps` or `events` across all namespaces using ClusterRoles.
