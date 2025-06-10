# Kubernetes - Vertical Pod Autoscaler (VPA)

This section covers how to configure and deploy a **Vertical Pod Autoscaler (VPA)** to automatically adjust CPU and memory resource requests for your Pods.

---

## 📁 File Overview

| File Name              | Description                                     |
|------------------------|-------------------------------------------------|
| nginx-deployment.yaml  | Sample deployment to apply VPA on               |
| vpa.yaml               | VPA definition for automatic resource tuning    |

---

## 🧠 Key Concepts

- **VPA** automatically adjusts `resources.requests` and `resources.limits` for containers.
- Helps optimize resource usage in long-running applications.
- VPA works by analyzing historical metrics and applying recommendations.

---

## ✅ Usage

### 1. Deploy the Application
```bash
kubectl apply -f nginx-deployment.yaml
```

### 2. Deploy the VPA Resource
```bash
kubectl apply -f vpa.yaml
```

### 3. Monitor VPA Recommendations
```bash
kubectl get vpa
kubectl describe vpa <vpa-name>
```

---

## 🔍 VPA Modes

VPA supports three modes:

- `"Off"` – only makes recommendations
- `"Initial"` – applies recommendations only at Pod creation
- `"Auto"` – automatically updates Pod resources (may cause restarts)

Check mode in `vpa.yaml`:
```yaml
updatePolicy:
  updateMode: "Auto"
```

---

## 📌 Notes

- VPA is **not compatible with HPA** when HPA is scaling based on resource metrics.
- Installing the VPA controller is required: https://github.com/kubernetes/autoscaler/tree/master/vertical-pod-autoscaler
- Use `kubectl describe vpa` to view resource recommendations over time.

---

🧠 Practice with different VPA modes and monitor resource tuning improvements using `kubectl top pods`.
