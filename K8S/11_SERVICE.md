## Service

A Service in Kubernetes provides a stable network endpoint to access one or more Pods. It allows communication between different components (e.g., frontend → backend) or access from outside the cluster.

**Why Do You Need a Service?**

the problem is 

In Kubernetes:
- You deploy your app (say nginx) using a Deployment.
- It creates multiple Pods (like small containers running your app).
- Each Pod gets its own IP address.
- But those IPs can change if the Pod restarts or gets rescheduled.

So, let’s say:
```
Pod-1 IP: 10.0.0.2
Pod-2 IP: 10.0.0.5
Pod-3 IP: 10.0.0.9
```
Tomorrow, they might be:
```
Pod-1 IP: 10.0.0.12
Pod-2 IP: 10.0.0.14
```

Why We Need a Service

A Service gives your app:
- A fixed name (e.g., nginx-service)
- A fixed IP inside the cluster (like 10.0.0.50)
- Automatically connects to whichever Pods are alive

So instead of calling:
```
http://10.0.0.2  
http://10.0.0.5 

#just call
http://nginx-service 
```

| Without Service                    | With Service                                         |
| ---------------------------------- | ---------------------------------------------------- |
| IPs change when Pods restart       | Fixed IP and name                                    |
| No easy way to reach your app      | Easy and stable access                               |
| No load balancing                  | Load balances between multiple Pods                  |
| Hard to expose app outside cluster | Can expose to internet using NodePort / LoadBalancer |

