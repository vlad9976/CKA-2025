# Kubernetes - Exposing Services (POD & Deployment)

This guide walks through different ways to expose Pods and Deployments using Kubernetes Services, including ClusterIP and NodePort types.

---

## 📁 File Overview

| File Name              | Description                                |
|------------------------|--------------------------------------------|
| service-despoyment.yaml| Deployment definition for service exposure |

---

## 🧠 Key Concepts

- **kubectl expose** command is used to generate service objects.
- Supports exposing individual Pods or Deployments.
- Use `--dry-run=client -o yaml` to preview a service manifest without creating it.
- Use `--type=NodePort` to allow external access via cluster node IP.

---

## ✅ Steps

### 🧱 Pre-Requisite Step 1: Create a Pod
```bash
kubectl run nginx --image=nginx
```

### 🧱 Pre-Requisite Step 2: Create a Deployment
```bash
nano service-deployment.yaml
kubectl apply -f service-deployment.yaml
```

---

### 🔧 Step 1: Expose a Pod via ClusterIP Service
```bash
kubectl expose pod nginx --name nginx-service --port=80 --target-port=80 --dry-run=client -o yaml
kubectl expose pod nginx --name nginx-service --port=80 --target-port=80 --dry-run=client -o yaml > service-01.yaml
kubectl describe service nginx-service
```

---

### 🌐 Step 2: Expose a Pod via NodePort Service
```bash
kubectl expose pod nginx --name nginx-nodeport-service --port=80 --target-port=80 --type=NodePort --dry-run=client -o yaml
kubectl get service
```

---

### 🚀 Step 3: Expose a Deployment via ClusterIP Service
```bash
kubectl expose deployment kplabs-deployment --name nginx-deployment-service --port=80 --target-port=8000
kubectl describe service nginx-deployment-service
```

---

### 🧹 Step 4: Cleanup Resources
```bash
kubectl delete pod nginx
kubectl delete deployment kplabs-deployment
kubectl delete service nginx-service
kubectl delete service nginx-nodeport-service
kubectl delete service nginx-deployment-service
```

---

## 📌 Notes

- The `kubectl expose` command is a fast way to expose existing Pods or Deployments via services.
- Use `--dry-run=client -o yaml` to preview the resource before creation.
- Use `kubectl expose --help` for full documentation on flags and options.

---

🧠 Experiment with different service types (ClusterIP, NodePort, LoadBalancer) to see how they behave in your environment!
