# Kubernetes - Gateway API (NGINX Gateway Controller)

This section demonstrates the use of the **Gateway API** with the **NGINX Gateway Fabric** as the controller.  
Gateway API is the future of ingress and service networking in Kubernetes, offering more powerful and expressive routing capabilities than traditional Ingress resources.

---

## 📁 File Overview

| File Name       | Description                                |
|------------------|--------------------------------------------|
| 2gateway.yaml     | Gateway resource configuration             |
| 4httproute.yaml   | HTTPRoute definition for service routing   |

---

## 🧠 Key Concepts

- **Gateway API** is a more flexible and extensible way to define traffic routing.
- A **GatewayClass** defines the controller handling gateways (like NGINX).
- A **Gateway** is like a load balancer.
- **HTTPRoute** defines rules for routing traffic to services based on hostname/path.

---

## ✅ Installation Steps

### 1. Install NGINX Gateway Controller

```bash
kubectl kustomize "https://github.com/nginx/nginx-gateway-fabric/config/crd/gateway-api/standard?ref=v1.6.2" | kubectl apply -f -
kubectl apply -f https://raw.githubusercontent.com/nginx/nginx-gateway-fabric/v1.6.2/deploy/crds.yaml
kubectl apply -f https://raw.githubusercontent.com/nginx/nginx-gateway-fabric/v1.6.2/deploy/default/deploy.yaml
```

---

### 2. Verify Deployment

```bash
kubectl get pods -n nginx-gateway
```

### 3. Check GatewayClass

```bash
kubectl get gatewayclass
kubectl describe gatewayclass nginx
```

---

## 🚀 Deploy and Expose a Service

```bash
kubectl create deployment apache --image=httpd:latest --port=80
kubectl expose deployment apache --name=apache-service --port=80 --target-port=80 --type=ClusterIP
```

---

## 🔧 Apply Gateway and HTTPRoute

```bash
kubectl apply -f 2gateway.yaml
kubectl apply -f 4httproute.yaml
```

---

## 🧪 Verify Routing

Test using curl or browser depending on Gateway IP and domain setup.

---

## 📌 Notes

- You may need to map a local domain (e.g., `echo.example.com`) in `/etc/hosts` to test routing via the Gateway IP.
- The NGINX Gateway Controller must support your Kubernetes version and Gateway API CRDs.

---

🧠 Practice building multi-route gateways and experiment with features like header-based routing or TLS!
