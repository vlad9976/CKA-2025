# Kubernetes - LoadBalancer Service Example

This section demonstrates how to use a **LoadBalancer Service** in Kubernetes.  
A LoadBalancer service exposes your application to external traffic by provisioning an external IP address (if supported by your environment/cloud).

---

## 📁 File Overview

| File Name        | Description                                |
|------------------|--------------------------------------------|
| lb-service.yaml  | Defines a LoadBalancer Service for a Pod/Pods |

---

## 🧠 Key Concepts

- **LoadBalancer** is a service type that routes external traffic to your Pods via an external IP.
- Supported only on cloud providers and environments that support external load balancers.
- Integrates with cloud infrastructure to provision load balancers automatically.

---

## ✅ Usage

Apply the LoadBalancer Service definition:
```bash
kubectl apply -f lb-service.yaml
```

Check the status of your Service and external IP:
```bash
kubectl get services
kubectl describe service <service-name>
```

Test access from outside the cluster (after external IP is assigned):
```bash
curl http://<external-ip>:<port>
```

Delete the Service:
```bash
kubectl delete -f lb-service.yaml
```

---

## 📌 Notes

- May take some time for the external IP to be assigned (watch `kubectl get services` for updates).
- Not all local clusters (e.g., minikube, kind) support LoadBalancer services natively.
- For development on local clusters, use `minikube tunnel` or MetalLB for LoadBalancer support.

---

🧠 Try exposing different workloads and see how cloud load balancers are provisioned!
