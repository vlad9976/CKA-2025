# Kubernetes - Manually Adding Pods to a Service (Without Labels)

This section demonstrates how to manually associate Pods with a Service **without relying on label selectors**.  
Instead, Pods are manually referenced using **Endpoints**, bypassing Kubernetes' default selector-based behavior.

---

## 📁 File Overview

| File Name                          | Description                                          |
|-----------------------------------|------------------------------------------------------|
| service.yaml                       | A Service with no selector                          |


---

## 🧠 Key Concepts

- Normally, a **Service** routes traffic to Pods using **label selectors**.
- If no selector is defined, you can **manually create an Endpoints object** to specify the target Pods (IP + port).
- This is useful in scenarios like:
  - Manually controlling traffic routing
  - Integrating legacy services
  - Service discovery across namespaces

---

## ✅ Usage

1. **Deploy backend and frontend Pods**:
   ```bash
   kubectl apply -f 1-backend
   kubectl apply -f 2-frontend
   ```

2. **Test direct communication (optional)**:
   ```bash
   kubectl apply -f 3-test-connection-B4-service
   ```

3. **Apply the Service without selector**:
   ```bash
   kubectl apply -f service.yaml
   ```

4. **Manually associate Endpoints**:
   ```bash
   kubectl apply -f Associate-Endpoints-with-Service.yaml
   ```

5. **Verify setup**:
   ```bash
   kubectl get endpoints
   kubectl get services
   ```

6. **Cleanup**:
   ```bash
   kubectl apply -f cleaneUP
   ```

---

## 📌 Notes

- When you create a Service **without a selector**, Kubernetes won’t manage the endpoints automatically.
- You must ensure the IP addresses and ports in the `Endpoints` object match the live Pods exactly.
- This is a more advanced but powerful way to decouple Services from their backing Pods.

---

🧠 Try using this approach to wrap external services or control traffic for debugging purposes!
