# Kubernetes - Named Port with NodePort Service

This section demonstrates how to use a **named port** in a Pod and reference it in a **NodePort Service**.  
Named ports enhance readability and reusability when defining services.

---

## 📁 File Overview

| File Name               | Description                              |
|--------------------------|------------------------------------------|
| named-port-pod.yaml      | Pod with a container exposing a named port |
| named-port-service.yaml  | NodePort Service referencing the named port |

---

## 🧠 Key Concepts

- **Named ports** are identifiers given to ports inside the container spec.
- In Services, you can refer to these names instead of numeric port values.
- This helps decouple the Pod configuration from the Service definition.

---

## ✅ Usage

1. Apply the Pod definition:
   ```bash
   kubectl apply -f named-port-pod.yaml
   ```

2. Apply the NodePort Service:
   ```bash
   kubectl apply -f named-port-service.yaml
   ```

3. Check service port assignment:
   ```bash
   kubectl get services
   ```

4. Access the service externally:
   ```bash
   curl http://<node-ip>:<node-port>
   ```

5. Delete resources:
   ```bash
   kubectl delete -f named-port-service.yaml
   kubectl delete -f named-port-pod.yaml
   ```

---

## 📌 Notes

- Named ports must match between the Pod and Service specs.
- Useful when multiple containers or applications use the same internal structure.
- Improves clarity in large deployments where numeric ports can be confusing.

---

🧠 Practice using named ports in other service types like ClusterIP or LoadBalancer for consistency!
