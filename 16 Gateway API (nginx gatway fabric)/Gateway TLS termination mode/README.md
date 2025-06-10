# Kubernetes - Gateway API with TLS Termination

This section shows how to configure **TLS termination** using the Kubernetes **Gateway API** and the NGINX Gateway Controller.  
TLS termination enables secure HTTPS access to services and terminates the TLS connection at the Gateway level.

---

## 📁 File Overview

| File Name                      | Description                                      |
|--------------------------------|--------------------------------------------------|
| 3termination-mode-gateway.yaml | Gateway definition with TLS termination          |
| 4httpRoute.yaml                | HTTPRoute for routing traffic to the service     |

---

## 🧠 Key Concepts

- TLS termination is configured on a **Gateway** with `tls` blocks specifying certificates and domain mappings.
- Requires a **TLS Secret** of type `kubernetes.io/tls` in the same namespace.
- The Gateway listens on port 443 (HTTPS) and forwards traffic to internal services securely.

---

## ✅ Setup Steps

### 1. Install NGINX Gateway Controller  
*(Skip if already installed)*  
Refer to: https://github.com/nginx/nginx-gateway-fabric

---

### 2. Create TLS Secret
```bash
kubectl create secret tls example-tls-secret \
  --cert=path/to/tls.crt \
  --key=path/to/tls.key \
  -n <namespace>
```

---

### 3. Deploy a Service (e.g., Apache)
```bash
kubectl create deployment apache --image=httpd:latest --port=80
kubectl expose deployment apache --name=apache-service --port=80 --target-port=80
```

---

### 4. Apply Gateway and HTTPRoute with TLS
```bash
kubectl apply -f 3termination-mode-gateway.yaml
kubectl apply -f 4httpRoute.yaml
```

---

### 5. Test HTTPS Access
Use curl or a browser (after mapping the hostname to the Gateway IP):

```bash
curl -k https://tls.example.com
```

Or map in `/etc/hosts`:
```
<gateway-ip> tls.example.com
```

---

## 📌 Notes

- Ensure the Gateway uses `https` listener with a valid `tls.secretName`.
- The secret must be in the same namespace as the Gateway.
- Use `curl -v` or browser dev tools to verify SSL/TLS negotiation.

---

🧠 Explore options for mutual TLS (mTLS), certificate rotation, and integration with cert-manager for auto-renewal.
