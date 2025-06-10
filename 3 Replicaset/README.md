# Kubernetes - ReplicaSet Example

This section demonstrates the use of a **ReplicaSet** in Kubernetes.  
A ReplicaSet ensures that a specified number of identical pod replicas are running at all times.

---

## 📁 File Overview

| File Name         | Description                      |
|-------------------|----------------------------------|
| replicaset.yaml   | Defines a Kubernetes ReplicaSet  |

---

## 🧠 Key Concepts

- **ReplicaSet** maintains a stable set of replica Pods.
- Automatically replaces Pods if they fail or are deleted.
- Useful for ensuring high availability and scaling stateless applications.

---

## ✅ Usage

Apply the ReplicaSet definition:
```bash
kubectl apply -f replicaset.yaml
```

Check the status of your ReplicaSet and Pods:
```bash
kubectl get replicaset
kubectl get pods
```

Describe your ReplicaSet:
```bash
kubectl describe replicaset <replicaset-name>
```

Delete the ReplicaSet:
```bash
kubectl delete -f replicaset.yaml
```

---

## 📌 Notes

- You can scale the number of replicas by editing the `replicas` field in the YAML file.
- The ReplicaSet will automatically create or remove Pods to match the desired state.

---

🧠 Practice by updating the image, labels, or replica count in the YAML file and observe how Kubernetes manages the Pods!
