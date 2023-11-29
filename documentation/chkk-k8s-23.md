---
title: Restrict assigning SYS_ADMIN linux capability to Pods and Containers
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Assign limited linux capabilities that strictly match the requirements of that Pod or Container.

```yaml sample-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: frontend
spec:
  containers:
    name: app
    image: images.my-company.example/app:v4
+   securityContext:
+     capabilities:
+       add:
-        - SYS_ADMIN
```

## Why does this exist? (Root Cause)

`SYS_ADMIN` capability provides root-level privileges to containers, thereby increasing the risk of attack by an unauthorized process.

## Affected Components

Containers and initContainers

## Additional Resources

For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/)