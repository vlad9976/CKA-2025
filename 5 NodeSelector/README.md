# Kubernetes - nodeSelector Example

This section demonstrates how to use the **nodeSelector** field in a Pod specification to schedule Pods onto specific nodes in your Kubernetes cluster.

---

## 📁 File Overview

| File Name                | Description                                    |
|--------------------------|------------------------------------------------|
| node-selector-pod.yaml   | Pod definition using nodeSelector              |

---

## 🧠 Key Concepts

- **nodeSelector** is used to constrain a Pod to run on particular nodes.
- The scheduler will only schedule the Pod on nodes that have the specified label.
- Useful for workloads requiring specific hardware, zones, or node types.

---

## ✅ Usage

1. **Label the target node** (if not already labeled):
   ```bash
   kubectl label nodes <node-name> <label-key>=<label-value>
   ```

2. **Apply the Pod definition:**
   ```bash
   kubectl apply -f node-selector-pod.yaml
   ```

3. **Verify where your Pod is scheduled:**
   ```bash
   kubectl get pods -o wide
   ```

4. **Remove the Pod:**
   ```bash
   kubectl delete -f node-selector-pod.yaml
   ```

---

## 📌 Notes

- If no node matches the nodeSelector, the Pod will remain in a Pending state.
- nodeSelector is the simplest node selection constraint—Kubernetes also supports node affinity for advanced scheduling.

---

🧠 Practice by labeling nodes with different attributes and updating your YAML accordingly!
