# Kubernetes - Custom Resource Definitions (CRDs)

This section covers **Custom Resource Definitions (CRDs)** in Kubernetes, which allow you to extend the Kubernetes API with your own resource types.

---

## 📁 File Overview

| File Name                      | Description                               |
|--------------------------------|-------------------------------------------|
| 1CustomResourceDefinition.yaml | CRD definition for a custom Kubernetes resource |

---

## 🧠 Key Concepts

- A **CRD** lets you define your own resource types in Kubernetes (e.g., `MyApp`, `Database`, `Alert`).
- Once created, you can manage custom resources using `kubectl` just like native objects.
- CRDs are the foundation for building Kubernetes Operators and custom controllers.

---

## ✅ Usage

### 1. Apply the CRD
```bash
kubectl apply -f 1CustomResourceDefinition.yaml
```

### 2. Verify the CRD is registered
```bash
kubectl get crds
kubectl describe crd <crd-name>
```

### 3. Create a custom resource (if provided)
```bash
kubectl apply -f my-custom-resource.yaml
```

### 4. View the custom resource
```bash
kubectl get <resource-kind>.<group>
kubectl describe <resource-kind> <name>
```

---

## 📌 Notes

- The CRD must specify `apiVersion`, `kind: CustomResourceDefinition`, and a `spec` with the new resource details.
- You can define **validation schemas**, **default values**, and **subresources** like `/status`.
- Combine CRDs with **controllers** to automate reconciliation logic (e.g., via Operators).

---

🧠 Practice by defining your own CRD and custom resource, then simulate a controller by reacting to changes using scripts or operators!
