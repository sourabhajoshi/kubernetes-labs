## DaemonSet

A DaemonSet ensures that one copy of a specific pod runs on every node in your Kubernetes cluster.

If you have 5 worker nodes, a DaemonSet will run 1 pod on each node automatically.

**Why is DaemonSet Important**

| Use Case               | Why DaemonSet is Needed                                      |
| ---------------------- | ------------------------------------------------------------ |
| **Node-level logging** | Run **Fluentd**, **Filebeat** to collect logs from all nodes |
| **Node monitoring**    | Run **Prometheus Node Exporter**, **Datadog agent**          |
| **Security agents**    | Install **antivirus**, **Falco**, etc. on all nodes          |
| **Network setup**      | Run **CNI plugins** like Calico, WeaveNet                    |
| **Storage management** | Deploy **Ceph**, **GlusterFS**, etc.                         |

**Block diagram of DaemonSet**

```
+-------------+     +-------------+     +-------------+
| Node 1      |     | Node 2      |     | Node 3      |
|-------------|     |-------------|     |-------------|
| DaemonSet → |     | DaemonSet → |     | DaemonSet → |
|  Pod        |     |  Pod        |     |  Pod        |
+-------------+     +-------------+     +-------------+

```

**Commands**
```
# List all DaemonSets
kubectl get daemonsets -A

# Describe a specific DaemonSet
kubectl describe ds <name> -n <namespace>

# Delete a DaemonSet
kubectl delete ds <name> -n <namespace>
```