# Kubernetes - Adapter Pattern (Sidecar)

This section illustrates the **Adapter Pattern** using a multi-container pod.  
The Adapter Pattern is a common Kubernetes design where a **sidecar container** is used to adapt or transform data for the main application container.

---

## 🧠 Key Concepts

- The Adapter (or Sidecar) container is paired with the main container in the same pod.
- It **modifies or enriches** input/output data before it reaches the main container or external systems.
- Both containers share:
  - **Network namespace** (communication via `localhost`)
  - **Volumes** (if needed for file exchange)

---

## 📁 Files Overview

| File Name              | Description                               |
|-----------------------|-------------------------------------------|
| adapter-pattern.yaml  | Demonstrates a pod using the adapter pattern |

---

## ✅ Usage

Apply the adapter pattern pod:
```bash
kubectl apply -f adapter-pattern.yaml
```

Inspect the pod and logs:
```bash
kubectl get pods
kubectl describe pod <pod-name>
kubectl logs <pod-name> -c <container-name>
```

Delete the pod:
```bash
kubectl delete -f adapter-pattern.yaml
```

---

## 📌 When to Use

Use the Adapter Pattern when you need to:
- Normalize or transform input data
- Inject monitoring/logging components
- Convert data formats between containers

---

🧠 Explore how the adapter interacts with the main container and practice extending this pattern for other integration tasks.
