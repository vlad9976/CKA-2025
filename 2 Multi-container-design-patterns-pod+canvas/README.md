# Kubernetes - Multi-Container Pods

This section focuses on **Multi-Container Pods** in Kubernetes.  
A pod in Kubernetes can encapsulate **one or more application containers**, along with shared resources such as **network, storage, and namespaces**.

---

## 🧠 Key Concepts

- A pod is the smallest deployable unit in Kubernetes.
- Multi-container pods share:
  - **Network namespace** (can talk via `localhost`)
  - **Storage volumes**
  - **Pod lifecycle and fate**

---

## 📁 Files Overview

| File Name                   | Description                             |
|----------------------------|-----------------------------------------|
| multi-containers pod.yaml  | Defines a pod with multiple containers  |

---

## ✅ Usage

Apply the multi-container pod definition:
```bash
kubectl apply -f multi-containers\ pod.yaml
```

Check running pods and describe details:
```bash
kubectl get pods
kubectl describe pod <pod-name>
```

Delete the pod:
```bash
kubectl delete -f multi-containers\ pod.yaml
```

---

## 📄 Reference Notes

> A pod in Kubernetes represents one or more application containers, and some shared resources for those containers.  
> A single pod can have multiple containers running  
> Shares: **Network, Namespace, Storage**

---

🧠 Keep practicing and exploring how containers interact inside a single pod.
