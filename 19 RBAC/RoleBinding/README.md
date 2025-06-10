# Kubernetes - RBAC (Role-Based Access Control)

This section introduces **RBAC (Role-Based Access Control)** in Kubernetes, which governs user and service permissions using defined roles and bindings.

---

## 📁 File Overview

| File Name            | Description                          |
|----------------------|--------------------------------------|
| 3role.yaml           | Defines a Role with specific rules   |
| 4role-binding.yaml   | Binds a user to the defined Role     |

---

## 🧠 Key Concepts

- **Roles** define **what actions** can be performed on which **resources** in a specific **namespace**.
- **RoleBindings** associate users (or service accounts) with a Role.
- Use **ClusterRoles** and **ClusterRoleBindings** for global access.

---

## ✅ Workflow

### 1. Create a Role (Namespace-Scoped)

Example from `3role.yaml`:

```yaml
kind: Role
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: pod-reader
  namespace: default
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get", "list"]
```

Apply it:
```bash
kubectl apply -f 3role.yaml
```

---

### 2. Bind the Role to a User

Example from `4role-binding.yaml`:

```yaml
kind: RoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: read-pods
  namespace: default
subjects:
- kind: User
  name: dev-user
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
```

Apply it:
```bash
kubectl apply -f 4role-binding.yaml
```

---

### 3. Verify Permissions

Switch to the user context (created via TLS auth or kubeconfig) and run:

```bash
kubectl auth can-i list pods
kubectl get pods
```

If permissions are correct, the user should succeed.

---

## 📌 Notes

- For cluster-wide permissions, use `ClusterRole` and `ClusterRoleBinding`.
- Avoid granting `*` verbs or resources unless absolutely necessary.
- RBAC is namespace-scoped unless you use Cluster-level resources.

---

🧠 Try combining multiple Roles and RoleBindings to simulate real multi-user access controls!
