## Pods

A Pod is the smallest and simplest deployable unit in Kubernetes.

- Pod = 1 or more containers + storage + network + configuration

So, a Pod is a wrapper around containers (usually just one), giving them:
- A unique IP address
- Shared storage
- Shared networking
- Configuration (like environment variables)
```
+-------------------------+
|         Pod             |
|  +-------------------+  |
|  |    Container(s)   |  |
|  +-------------------+  |
|  |   Shared Storage  |  |
|  |   Shared Network  |  |
|  +-------------------+  |
+-------------------------+

```

### Why are Pods important?

| Reason                                  | Explanation                                                                                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| **Fundamental Unit**                    | All applications in Kubernetes run inside Pods — whether it's a single container or multiple working together. |
| **Manages Lifecycle**                   | Kubernetes manages the lifecycle of Pods — creating, restarting, or removing them.                             |
| **Encapsulation**                       | Pods encapsulate all the resources a containerized app needs to run.                                           |
| **Building Block for Higher Resources** | Deployments, ReplicaSets, StatefulSets, and DaemonSets all **manage Pods** under the hood.                     |

### **How Pods are linked to other Kubernetes components**

| Component              | Relationship to Pod                                         |
| ---------------------- | ----------------------------------------------------------- |
| **Deployment**         | Manages ReplicaSets → which manage multiple Pods            |
| **ReplicaSet**         | Ensures a specific number of Pod replicas are running       |
| **StatefulSet**        | Manages Pods with **stable identity** (for databases, etc.) |
| **DaemonSet**          | Ensures a Pod runs on **every node**                        |
| **Job / CronJob**      | Create Pods for batch or scheduled tasks                    |
| **Service**            | Exposes Pods on the network (load balances traffic to Pods) |
| **ConfigMap / Secret** | Injects config or sensitive data into Pods                  |
| **PVC / Storage**      | Mounts volumes inside Pods for persistent data              |
| **NetworkPolicy**      | Controls which Pods can talk to each other                  |
| **Probes**             | Check Pod health (liveness/readiness)                       |
| **ServiceAccount**     | Provides Pods with permissions (RBAC)                       |

## How to write a Pod YAML (Step-by-Step)



---
yaml in k8s : k8s definition file always conatin 4 properties : apiversions, kind, metadata, spec