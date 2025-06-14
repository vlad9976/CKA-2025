# Kubernetes - Resource Limits & Requests Example

This section demonstrates how to use **resource requests and limits** in Kubernetes Pod specifications to manage CPU and memory usage.

---

## 📁 File Overview

| File Name                        | Description                                  |
|----------------------------------|----------------------------------------------|
| resource-limit-basic.yaml        | Basic resource limits for CPU/memory         |
| resource-limit-create-requests.yaml | Resource requests along with limits         |
| resource-limit-pending-state.yaml| Pod pending due to unsatisfiable requests    |
| resource-limit-resource-error.yaml| Pod fails due to exceeding limits           |

---

## 🧠 Key Concepts

- **Requests**: Minimum amount of CPU/memory guaranteed to the container.
- **Limits**: Maximum amount of CPU/memory a container can use.
- If a Pod tries to use more than the limit, it may be throttled (CPU) or killed (memory).
- If there aren't enough resources to satisfy requests, Pod will remain in Pending state.

---

## ✅ Usage

Apply a resource-limited Pod definition:
```bash
kubectl apply -f resource-limit-basic.yaml
```

Check Pod status and resource usage:
```bash
kubectl get pods
kubectl describe pod <pod-name>
kubectl top pod <pod-name>
```

Delete the Pod:
```bash
kubectl delete -f resource-limit-basic.yaml
```

Test error or pending behavior:
- Try applying `resource-limit-pending-state.yaml` or `resource-limit-resource-error.yaml` to see scheduler and OOM responses.

---

## 📌 Notes

- Setting only **limits** may cause unpredictable scheduling. Always set **requests** and **limits** for production workloads.
- Resource quotas and limits are essential for multi-tenant clusters.

---

🧠 Practice by adjusting CPU and memory values and observing how scheduling and resource management work!
