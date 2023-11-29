---
title: Tiller (Helm V2) should not be accessible inside the K8s cluster
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Go Tillerless and use Helm v3

```yaml sample-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: frontend
spec:
  containers:
    name: app
-   image: tiller
```

## Why does this exist? (Root Cause)

Tiller violates the principle of least privilege as it comes with a broad range of permissions to access Kubernetes API server.

## Affected Components

Containers and initContainers

## Additional Resources

For more details on using Helm v3, please refer to the [official Helm documentation] \(<https://helm.sh>)