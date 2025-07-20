
---

## ☸️ Kubernetes Interview Notes

### 1. **What is Kubernetes?**

* Open-source container orchestration platform for automating deployment, scaling, and management of containerized applications.
* Developed by Google, now maintained by CNCF (Cloud Native Computing Foundation).

---

### 2. **Core Concepts**

| Term           | Description                                                       |
| -------------- | ----------------------------------------------------------------- |
| **Cluster**    | Group of machines (nodes) running Kubernetes.                     |
| **Node**       | Worker machine (physical or VM) in a cluster.                     |
| **Pod**        | Smallest deployable unit in K8s. Contains one or more containers. |
| **Deployment** | Manages rollout, scaling, and self-healing of pods.               |
| **Service**    | Abstraction to expose pods via stable IP/port.                    |
| **Namespace**  | Virtual cluster within a cluster for isolation.                   |

---

### 3. **Basic Architecture**

```
Cluster
├── Master Node (Control Plane)
│   ├── API Server
│   ├── Controller Manager
│   ├── Scheduler
│   └── etcd (key-value store)
└── Worker Nodes
    ├── kubelet
    ├── Container Runtime (e.g., containerd, Docker)
    └── kube-proxy
```

---

### 4. **YAML Example: Deployment + Service**

```yaml
# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp
spec:
  replicas: 2
  selector:
    matchLabels:
      app: webapp
  template:
    metadata:
      labels:
        app: webapp
    spec:
      containers:
      - name: app
        image: myapp:latest
        ports:
        - containerPort: 5000
```

```yaml
# service.yaml
apiVersion: v1
kind: Service
metadata:
  name: webapp-service
spec:
  selector:
    app: webapp
  ports:
  - port: 80
    targetPort: 5000
  type: NodePort
```

---

### 5. **K8s Objects**

* **Pod**: Runs container(s) with shared storage/network.
* **ReplicaSet**: Ensures N identical pods are running.
* **Deployment**: Manages ReplicaSet, updates, rollbacks.
* **Service**: Access pods via internal IP.
* **ConfigMap**: Externalize configuration (plain key-value).
* **Secret**: Store sensitive data (base64 encoded).
* **Ingress**: HTTP/HTTPS routing to services.
* **Volume**: Persistent or ephemeral storage.

---

### 6. **Types of Services**

| Type         | Purpose                              |
| ------------ | ------------------------------------ |
| ClusterIP    | Default, internal access only        |
| NodePort     | Exposes service on port on each Node |
| LoadBalancer | Uses cloud provider’s load balancer  |
| ExternalName | Maps service to external DNS name    |

---

### 7. **Commands**

```bash
# Cluster info
kubectl cluster-info

# Deployments and pods
kubectl get deployments
kubectl get pods

# Apply config
kubectl apply -f deployment.yaml

# Logs and exec
kubectl logs <pod-name>
kubectl exec -it <pod-name> -- bash

# Delete resources
kubectl delete -f deployment.yaml
```

---

### 8. **Useful Concepts**

* **Labels & Selectors**: Key-value pairs to organize and target K8s objects.
* **Taints & Tolerations**: Control which pods run on which nodes.
* **Node Affinity**: Schedule pods to specific nodes based on labels.
* **Probes**:

  * Liveness: restart container if unhealthy.
  * Readiness: wait before routing traffic.
* **Horizontal Pod Autoscaler**: Auto-scale based on CPU/memory metrics.

---

### 9. **Helm (Brief Intro)**

* Package manager for Kubernetes.
* Helm Chart = pre-configured K8s resources.

```bash
helm install myapp ./mychart
helm upgrade myapp ./mychart
helm uninstall myapp
```

---

### 10. **Interview Questions**

* What happens when you apply a Deployment YAML?
* Difference between ReplicaSet and Deployment?
* How does Service discovery work in Kubernetes?
* How do you persist data in Kubernetes?
* What’s the difference between a ConfigMap and a Secret?
* Explain liveness and readiness probes.
* How does Kubernetes handle rolling updates?

---

Let me know if we move to **Jenkins** next, or if you want a `.pdf` combining Docker + Kubernetes so far.
