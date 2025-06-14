# Kubernetes - Pods Section

Welcome to the **Kubernetes Pods** practice section.  
This directory includes YAML manifests and configurations focused on creating and managing **Pods** in Kubernetes.

---

## 📁 Files Overview

| File Name               | Description                             |
|------------------------|-----------------------------------------|
| pod.yaml               | Basic pod definition                    |
| pod2.yaml              | Another basic pod example               |
| named-pod.yaml         | Pod with a specified name               |
| label-pod.yaml         | Pod with labels                         |
| 3-labled-pods.yaml     | Multiple pods with labels               |
| command-definition.yaml| Pod with custom command                 |
| Exposing-port.yaml     | Pod definition exposing a container port|
| pod-expose-port.yaml   | Expose pod port using service definition|

---

## ✅ Usage

Apply a configuration:
```bash
kubectl apply -f <filename>.yaml
```

Check pod status:
```bash
kubectl get pods
```

Delete a resource:
```bash
kubectl delete -f <filename>.yaml
```

---

## 📌 Notes

These files are part of the Kubernetes **Pods** learning module.  
They are for hands-on practice and are not intended for production environments.

---

🧠 Happy Learning!

---

## 📝 Pod Manifest Examples & Commands

### **pod.yaml**
```yaml
apiVersion: v1
kind: pod
metadata:
  name: mywebserver
spec:
  containers:
    - name: mywebserver
      image: nginx
```
- `apiVersion` = Version of API  
- `kind` = Kind of object you want to create  
- `metadata` = Name of object that uniquely identifies it  
- `name`  
- `spec` = Desired state of the object

### **kubectl**
```bash
# Create pod from yaml file
kubectl apply -f pod.yaml

# Delete everything that is part of the yaml file
kubectl delete -f pod.yaml
```

### **Generating Pod Manifests via CLI**
```bash
# 1. Create a Pod from Nginx Image
kubectl run nginx --image=nginx

# 2. Create a Pod and Expose a Port
kubectl run nginx-port --image=nginx --port=80

# 3. Output the Manifest File
kubectl run nginx --image=nginx --port=80 --dry-run=client -o yaml

# 4. Delete PODS
kubectl delete pod nginx
kubectl delete pod --all
```

### **Expose-pod.yaml**
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
spec:
  containers:
  - image: nginx
    name: democontainer
    ports:
      - containerPort: 8080
```
> List of ports to expose from the container.  
> Not specifying a port here DOES NOT prevent that port from being exposed.  
> Any port which is listening on the default "0.0.0.0" address inside a container will be accessible from the network.
