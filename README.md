# Kubernetes Learning Roadmap

## 1. Basics & Foundations  
- Cluster & Nodes** → Understand what a cluster is (control plane + worker nodes).
- kubectl → Practice basic commands (`get`, `describe`, `create`, `delete`).
- Namespaces → Logical grouping of resources.

**Practice**

Create a namespace and run a simple pod.

```bash
kubectl create ns demo
kubectl run nginx --image=nginx -n demo
kubectl get pods -n demo
```
## 2. Pods (the smallest unit)
- What is a Pod? → A wrapper around one or more containers.  
- Multi-container pods → Sidecar pattern.
- Pod lifecycle & restart policies.

**Practice**

Create a Pod YAML and run it.

## 3. Workloads (Controllers that manage pods)

- Deployment → stateless apps, scaling, rolling updates.
- ReplicaSet → ensures desired number of pods.
- StatefulSet → stateful apps (databases, need stable identity).
- DaemonSet → runs a pod on every node (e.g., logging agent).
- Job & CronJob → one-time or scheduled tasks.

**Practice**

Deploy an Nginx deployment, scale it up/down.

## 4. Services (Networking)

- ClusterIP (default, internal access).
- NodePort (exposes service on node IP/port).
- LoadBalancer (cloud provider integration).
- Ingress (routes HTTP/HTTPS traffic, reverse proxy).

**Practice**

Expose your Nginx app with a Service → then add Ingress.

## 5. Config & Secrets

- ConfigMap → store app configs.
- Secret → store sensitive data (passwords, tokens).
- Downward API → pass metadata like Pod name, namespace.

**Practice**

Inject a ConfigMap and Secret into your Deployment.

## 6. Storage

- PersistentVolume (PV) → actual storage resource.
- PersistentVolumeClaim (PVC) → request storage for a pod.
- StorageClass → dynamic provisioning of volumes.
- StatefulSet + PVC → database example.

**Practice**

Create a PVC, attach it to a pod, and check data persistence.

## 7. Security & Access

- RBAC (Role-Based Access Control) → Roles, ClusterRoles, RoleBindings.
- ServiceAccount → identity for pods.
- NetworkPolicies → control traffic between pods.

## 8. Observability & Tools

- Events & Logs (kubectl logs, kubectl describe).
- Probes → liveness, readiness, startup.
- Resource Limits (requests & limits).
- Monitoring & Metrics (Prometheus, Grafana, Lens, K9s).

## 9. Advanced (when you’re ready)

- Helm → package manager for Kubernetes.
- Operators & CRDs → extend Kubernetes.
- CNI plugins (Calico, Flannel) → networking.
- CNI / CSI drivers → storage & networking extensions.
- GitOps (ArgoCD, Flux) → deploy apps via Git.
