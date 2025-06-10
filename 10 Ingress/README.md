# Kubernetes - Ingress Examples

This section provides examples of how to create and manage **Ingress resources** in Kubernetes.  
Ingress allows you to route HTTP and HTTPS traffic to multiple services within the cluster using a single external IP or DNS.

---

## 📁 File Overview

| File Name                              | Description                                     |
|----------------------------------------|-------------------------------------------------|
| ingress.yaml                           | Basic ingress definition                        |
| name-based-virtual-hosting-Ingress.yaml| Ingress with name-based virtual hosting         |
| path-based-ingress.yaml                | Ingress routing based on request paths          |
| named-and-path-ingress.yaml            | Ingress combining name-based and path-based rules |

---

## 🧠 Key Concepts

- Ingress controllers must be installed (e.g., NGINX Ingress Controller).
- Ingress resources define routing rules based on hostnames and/or paths.
- Enables centralized routing, TLS termination, and cleaner service access.

---

## ✅ Commands

### 📘 Check Help
```bash
kubectl create ingress --help
```

---

### 🌐 Create Ingress with One Rule
```bash
kubectl create ingress first-ingress --rule="example.internal/*=example-service:80"
kubectl describe ingress first-ingress
```

---

### 🌐 Create Ingress with Multiple Rules
```bash
kubectl create ingress second-ingress \
  --rule="example.internal/*=example-service:80" \
  --rule="kplabs.internal/*=kplabs-service:80"
```

---

## 🔍 Verifying

Check ingress objects:
```bash
kubectl get ingress
kubectl describe ingress <ingress-name>
```

Test access (depending on your ingress controller setup):
```bash
curl -H "Host: example.internal" http://<ingress-controller-ip>
```

---

## 📌 Notes

- Ingress controllers are not included by default. You must install one (e.g., NGINX, Traefik).
- DNS entries like `example.internal` must resolve to your ingress controller (via `/etc/hosts` or internal DNS).
- Use `kubectl apply -f <file>` to deploy YAML-based configurations for more control.

---

🧠 Practice combining name-based and path-based rules to simulate real-world service routing!
