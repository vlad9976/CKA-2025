# Kubernetes - Deployment Example

This section demonstrates the use of a **Deployment** in Kubernetes.  
A Deployment manages ReplicaSets and provides declarative updates for Pods and ReplicaSets, enabling easy scaling, rolling updates, and rollbacks.

---

## 📁 File Overview

| File Name        | Description                    |
|------------------|-------------------------------|
| deployment.yaml  | Defines a Kubernetes Deployment|

---

## 🧠 Key Concepts

- **Deployment** ensures the desired state for your Pods and ReplicaSets.
- Supports rolling updates and rollbacks.
- Simplifies application scaling and version upgrades.

---

## ✅ Usage

Apply the Deployment definition:
```bash
kubectl apply -f deployment.yaml
```

Check the status of your Deployment, ReplicaSets, and Pods:
```bash
kubectl get deployments
kubectl get replicasets
kubectl get pods
```

Describe your Deployment:
```bash
kubectl describe deployment <deployment-name>
```

Delete the Deployment:
```bash
kubectl delete -f deployment.yaml
```

---

## 📌 Notes

- You can scale the number of replicas by editing the `replicas` field in the YAML file or using:
  ```bash
  kubectl scale deployment <deployment-name> --replicas=5
  ```
- For rolling updates, modify the image version in the YAML and re-apply.
- You can rollback to a previous version if needed.

---

🧠 Practice by updating the image, labels, or replica count in the YAML file and observe how Kubernetes manages the application!
