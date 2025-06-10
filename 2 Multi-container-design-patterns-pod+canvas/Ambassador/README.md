# Kubernetes - Ambassador Adapter Pattern

This section demonstrates the **Ambassador Adapter Pattern** in Kubernetes.  
This hybrid pattern combines the **Ambassador** and **Adapter** (Sidecar) patterns to proxy and transform data between your application and external services.

---

## 🧠 Key Concepts

- **Ambassador** container acts as a proxy between your application and external HTTP services.
- **Adapter** container transforms or enriches data before it reaches the application.
- Both sidecar containers share:
  - **Network namespace** (communication via `localhost`)
  - **Volumes** (for file-based data exchange, if needed)

---

## 📁 Files Overview

| File Name                       | Description                                              |
|---------------------------------|----------------------------------------------------------|
| ambassador-adapter-pattern.yaml | Pod with ambassador proxy and adapter transformation     |

---

## ✅ Usage

Apply the pod definition:
```bash
kubectl apply -f ambassador-adapter-pattern.yaml
```

Verify pods and logs:
```bash
kubectl get pods
kubectl describe pod ambassador-example
kubectl logs ambassador-example -c ambassador
kubectl logs ambassador-example -c adapter
```

Delete the pod:
```bash
kubectl delete -f ambassador-adapter-pattern.yaml
```

---

## 📌 When to Use

Use this pattern when you need to:
- Offload communication with external services.
- Normalize or transform external data before your app consumes it.
- Centralize proxy logic and data adaptation in reusable sidecars.

---

🧠 Try customizing the sidecars for different protocols and transformations.
