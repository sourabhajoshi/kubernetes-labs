## ConfigMap

A ConfigMap is a Kubernetes object used to store non-sensitive configuration data in key-value pairs.

Think of it like a config file (e.g., .env, config.json) — but managed inside your Kubernetes cluster.

**Why Use ConfigMap**
- Decouple configuration from code.
- Change config without rebuilding container images.
- Reuse config across multiple pods or applications.
- Can be mounted as files or used as environment variables in Pods.

**Sample ConfigMap YAML**

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: my-config          # Name of the ConfigMap
  namespace: default       # Optional namespace
data:
  APP_NAME: "WeSim App"    # Key-value pair 1
  APP_ENV: "production"    # Key-value pair 2
  APP_PORT: "8080"         # Key-value pair 3
```

**How to Use ConfigMap in a Pod**

As Environment Variables:
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: app-pod
spec:
  containers:
    - name: myapp
      image: nginx
      envFrom:
        - configMapRef:
            name: my-config  # Reference the ConfigMap
```

| Feature     | ConfigMap                | Secret                                |
| ----------- | ------------------------ | ------------------------------------- |
| Purpose     | Store non-sensitive data | Store sensitive data (e.g., password) |
| Encoded?    | No                       | Yes (Base64-encoded)                  |
| Use in pods | Env var / volume         | Same                                  |
