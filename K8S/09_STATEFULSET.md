## StatefulSet

A StatefulSet is a Kubernetes controller that manages the deployment and scaling of Pods where each Pod:
- Has a stable identity
- Keeps its data even after restarting
- Starts and stops in a specific order

This is important for apps like databases, message brokers, and distributed systems (e.g., Kafka, Cassandra).

**How is it different from a Deployment?**

| Feature            | Deployment        | StatefulSet               |
| ------------------ | ----------------- | ------------------------- |
| Pod names          | Random            | Predictable (e.g., `web-0`) |
| Persistent Storage | Shared or Ephemeral | Unique for each Pod       |
| Ordered Start/Stop | No                | Yes (one by one)          |
| Use Case           | Stateless apps    | Stateful apps             |

**Stateful component**
```yaml
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: my-db
spec:
  serviceName: "my-db-headless"  # Headless service is required
  replicas: 3
  selector:
    matchLabels:
      app: my-db
  template:
    metadata:
      labels:
        app: my-db
    spec:
      containers:
      - name: my-db
        image: postgres:15
        volumeMounts:
        - name: data
          mountPath: /var/lib/postgresql/data
  volumeClaimTemplates:         # Template to request per-pod PVC
  - metadata:
      name: data
    spec:
      accessModes: ["ReadWriteOnce"]
      resources:
        requests:
          storage: 1Gi
```

**Commands**
```
# Create StatefulSet
kubectl apply -f statefulset.yaml

# List pods
kubectl get pods -l app=my-db

# Get PVCs created by StatefulSet
kubectl get pvc

# Scale StatefulSet
kubectl scale statefulset my-db --replicas=5

```