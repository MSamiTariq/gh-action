---
title: Containers should not be Privileged
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Set `securityContext.privileged` to `false`

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
+     privileged: false
```

## Why does this exist? (Root Cause)

If a privileged container is compromised, an attacker will be able to run full host root with all of the available capabilities, including `CAP_SYS_ADMIN`

## Affected Components

Containers and initContainers

## Additional Resources

For more details, please refer to the [official Kubernetes documentation.](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/)