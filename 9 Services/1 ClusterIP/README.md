# Kubernetes - ClusterIP Service Example

This section demonstrates how to use a **ClusterIP Service** in Kubernetes.  
A ClusterIP service provides a stable, internal IP address for exposing one or more Pods within the cluster.

---

## 📁 File Overview

| File Name          | Description                                 |
|--------------------|---------------------------------------------|
| test-service.yaml  | Defines a ClusterIP Service for a Pod/Pods  |

---

## 🧠 Key Concepts

- **ClusterIP** is the default service type; it exposes the service on an internal IP only accessible within the cluster.
- Used for internal communication between microservices.
- Service routes traffic to Pods based on label selectors.

---

## ✅ Usage

Apply the ClusterIP Service definition:
```bash
kubectl apply -f test-service.yaml
```

Check the status of your Service and endpoints:
```bash
kubectl get services
kubectl describe service <service-name>
kubectl get endpoints
```

Test connectivity from within the cluster (e.g., from another Pod):
```bash
kubectl exec -it <pod-name> -- curl http://<service-name>:<port>
```

Delete the Service:
```bash
kubectl delete -f test-service.yaml
```

---

## 📌 Notes

- ClusterIP services are not accessible from outside the cluster. For external access, use NodePort or LoadBalancer.
- Make sure Pods matched by the service selector are running.

---

🧠 Practice creating services for different workloads and explore service discovery within your cluster!
