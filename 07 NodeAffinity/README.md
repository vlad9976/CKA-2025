# Kubernetes - Node Affinity Example

This section demonstrates how to use **Node Affinity** in Kubernetes to control Pod scheduling based on node labels, providing more advanced scheduling options than nodeSelector.

---

## 📁 File Overview

| File Name                     | Description                                       |
|-------------------------------|---------------------------------------------------|
| nodeaffinity-requered.yaml    | Pod using requiredDuringSchedulingIgnoredDuringExecution (hard rule) |
| nodeAffinity-prefered.yaml    | Pod using preferredDuringSchedulingIgnoredDuringExecution (soft rule)|

---

## 🧠 Key Concepts

- **Node Affinity** allows fine-grained scheduling of Pods using node labels.
- `requiredDuringSchedulingIgnoredDuringExecution` is a **hard requirement**; the Pod will only schedule on nodes matching all rules.
- `preferredDuringSchedulingIgnoredDuringExecution` is a **soft preference**; the scheduler tries to honor, but will schedule elsewhere if needed.
- Useful for ensuring workloads land on nodes with specific hardware, zones, or characteristics.

---

## ✅ Usage

1. **Label your nodes** (if not already labeled):
   ```bash
   kubectl label nodes <node-name> <label-key>=<label-value>
   ```

2. **Apply the Pod definition (hard affinity):**
   ```bash
   kubectl apply -f nodeaffinity-requered.yaml
   ```

   **Apply the Pod definition (soft affinity):**
   ```bash
   kubectl apply -f nodeAffinity-prefered.yaml
   ```

3. **Check where your Pod is scheduled:**
   ```bash
   kubectl get pods -o wide
   ```

4. **Delete the Pod:**
   ```bash
   kubectl delete -f nodeaffinity-requered.yaml
   kubectl delete -f nodeAffinity-prefered.yaml
   ```

---

## 📌 Notes

- Node Affinity is preferred over nodeSelector for advanced scheduling logic.
- Combine node affinity with other scheduling constraints for complex environments.

---

🧠 Try using both hard and soft affinity rules and observe the scheduler’s behavior in your cluster!
