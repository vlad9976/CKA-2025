# Kubernetes - Adapter Pattern

This section illustrates the **Adapter Pattern** in Kubernetes using a sidecar container.  
The Adapter Pattern uses a **sidecar container** to transform or enrich data for the main application container.

---

## 🧠 Key Concepts

- A **main application container** serves your core workload.
- A **sidecar container** (Adapter) runs alongside to:
  - Transform or enrich data (e.g., format conversion, data filtering).
  - Provide auxiliary features (e.g., logging, monitoring).
- Both containers share:
  - **Network namespace** – communicate via `localhost`.
  - **Volumes** – for file-based data exchange.

---

## 📁 Files Overview

| File Name             | Description                               |
|-----------------------|-------------------------------------------|
| adapter-pattern.yaml  | Pod definition demonstrating the Adapter Pattern |

---

## ✅ Usage

Apply the adapter pattern pod:
```bash
kubectl apply -f adapter-pattern.yaml
```

Inspect the pod and logs:
```bash
kubectl get pods
kubectl describe pod adapter-example
kubectl logs adapter-example -c main-app
kubectl logs adapter-example -c adapter
```

Delete the pod:
```bash
kubectl delete -f adapter-pattern.yaml
```

---

## 📌 When to Use

Use the Adapter Pattern when you need to:
- Transform or normalize data before it reaches your main application.
- Offload auxiliary tasks such as logging, metrics, or data formatting.
- Keep your main application container lightweight and focused.

---

🧠 Practice by extending the adapter logic for different data transformations.
