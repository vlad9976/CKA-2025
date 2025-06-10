# Kubernetes - NodePort Service Example

This section demonstrates how to use a **NodePort Service** in Kubernetes.  
A NodePort service exposes your application on a static port across each node’s IP in your cluster, allowing external access.

---

## 📁 File Overview

| File Name         | Description                               |
|-------------------|-------------------------------------------|
| nodeport.yaml     | Defines a NodePort Service                |
| enother-nodeport.yaml | (Alternative) NodePort Service example|

---

## 🧠 Key Concepts

- **NodePort** exposes the service on a static port on each Node IP.
- Traffic from `<NodeIP>:<NodePort>` is forwarded to the underlying Pods.
- Useful for simple external access or development/testing environments.

---

## ✅ Usage

Apply the NodePort Service definition:
```bash
kubectl apply -f nodeport.yaml
```

Check the status and external port:
```bash
kubectl get services
kubectl describe service <service-name>
```

Test access (replace <node-ip> and <node-port> with actual values):
```bash
curl http://<node-ip>:<node-port>
```

Delete the Service:
```bash
kubectl delete -f nodeport.yaml
```

---

## 📌 Notes

- NodePort range is typically 30000-32767.
- You can access the service using any node’s external or internal IP address and the assigned port.
- For production, prefer LoadBalancer or Ingress for greater flexibility.

---

🧠 Practice by exposing different services and try accessing them from outside your cluster!
