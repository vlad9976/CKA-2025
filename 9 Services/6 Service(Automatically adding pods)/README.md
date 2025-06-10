# Kubernetes - Automatically Adding Pods to a Service (Using Label Selectors)

This section demonstrates how to **automatically associate Pods with a Service** using Kubernetes’ built-in **label selectors**.

---

## 📁 File Overview

| File Name               | Description                                 |
|--------------------------|---------------------------------------------|
| demo-deployment.yaml     | Deployment that creates Pods with labels    |
| service-selector.yaml    | Service that uses a selector to auto-link to Pods |

---

## 🧠 Key Concepts

- Kubernetes Services use **label selectors** to find matching Pods.
- When the label on a Pod matches the selector in a Service, traffic is routed automatically.
- This is the default and most common method for connecting Pods to Services.

---

## ✅ Usage

1. **Deploy the application Pods** via Deployment:
   ```bash
   kubectl apply -f demo-deployment.yaml
   ```

2. **Create the Service with selector**:
   ```bash
   kubectl apply -f service-selector.yaml
   ```

3. **Check status and verify link**:
   ```bash
   kubectl get pods --show-labels
   kubectl get services
   kubectl get endpoints
   ```

4. **Test connectivity** (e.g., via port-forward or curl from another Pod):
   ```bash
   kubectl port-forward service/<service-name> <local-port>:<service-port>
   ```

5. **Cleanup**:
   ```bash
   kubectl delete -f service-selector.yaml
   kubectl delete -f demo-deployment.yaml
   ```

---

## 📌 Notes

- Pods created by Deployments or ReplicaSets automatically inherit labels.
- Services track these labels to dynamically adjust traffic routing.
- If Pods don’t match the selector, the Service will have no endpoints.

---

🧠 Practice by adjusting labels or selector fields and observe how traffic routing changes!
