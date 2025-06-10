# Kubernetes - Horizontal Pod Autoscaler (HPA)

This section covers how to configure and deploy a **Horizontal Pod Autoscaler (HPA)** to automatically scale Pods based on CPU or memory utilization.

---

## 📁 File Overview

| File Name                         | Description                                         |
|----------------------------------|-----------------------------------------------------|
| hpa-deployment-example.yaml      | Sample deployment to be autoscaled                 |
| hpa-stabilization.yaml           | HPA config with stabilization window               |
| hpa-stabilization-windows-deploy.yaml | Windows-based deployment for HPA tests         |

---

## 🧠 Key Concepts

- **HPA** automatically adjusts the number of Pod replicas based on observed CPU/memory usage or custom metrics.
- Relies on the **Metrics Server** to collect usage statistics.
- Scaling decisions can be smoothed with a **stabilization window** to avoid flapping.

---

## ✅ Usage

### 1. Deploy the Application
```bash
kubectl apply -f hpa-deployment-example.yaml
```

### 2. Create HPA Resource
```bash
kubectl autoscale deployment <deployment-name> --cpu-percent=50 --min=1 --max=10
```

Or apply manually:
```bash
kubectl apply -f hpa-stabilization.yaml
```

### 3. Monitor the HPA
```bash
kubectl get hpa
kubectl describe hpa <hpa-name>
```

### 4. Simulate Load
```bash
kubectl exec -it <pod-name> -- sh
# Inside pod: while true; do :; done
```

### 5. Watch Scaling
```bash
kubectl get hpa -w
```

---

## 📌 Notes

- Requires Metrics Server to be running.
- Use `kubectl top pods` to verify metric availability.
- `stabilizationWindowSeconds` can be used to delay scaling decisions for stability.

---

🧠 Try setting up HPA with both CPU and memory targets, and experiment with minimum/maximum bounds!
