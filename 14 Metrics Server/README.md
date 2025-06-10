# Kubernetes - Metrics Server

This section covers the deployment and usage of the **Metrics Server** in Kubernetes.  
The Metrics Server collects resource metrics like CPU and memory usage from Kubelets and exposes them via the Kubernetes API.

---

## 🔗 Reference

- Metrics Server GitHub: https://github.com/kubernetes-sigs/metrics-server

---

## ✅ Deploy Metrics Server

To deploy the Metrics Server using a public manifest:

```bash
kubectl apply -f https://raw.githubusercontent.com/zealvora/certified-kubernetes-administrator/refs/heads/master/Domain%203%20-%20Services%20and%20Networking/metric-server.yaml
```

---

## 🔍 Verify Metrics Collection

View resource usage of Pods:
```bash
kubectl top pods
kubectl top pods -A  # all namespaces
```

View resource usage of Nodes:
```bash
kubectl top nodes
```

---

## 🧠 Key Concepts

- The Metrics Server provides resource usage metrics for:
  - **Pods**
  - **Nodes**
- It is required for:
  - **Horizontal Pod Autoscaler (HPA)**
  - **kubectl top** commands
- It does **not** persist historical metrics (use Prometheus/Grafana for that).

---

## 📌 Notes

- Ensure the Metrics Server has proper API access and the API server allows secure communication (`--kubelet-insecure-tls` is common in demos).
- Metrics Server must run in the same network as your kubelets and have access to their `/metrics` endpoints.
- It is **not a full monitoring solution**, but a lightweight metrics endpoint provider.

---

🧠 Once metrics are available, try deploying an HPA or visualizing metrics with tools like Lens or K9s.
