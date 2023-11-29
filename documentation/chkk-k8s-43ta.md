---
title: Minimize the admission of containers with capabilities assigned
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Assign capabilities to containers within the default set.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: <Pod name>
spec:
  containers:
  - name: app
    image: images.my-company.example/app:v4
    securityContext:
      capabilities:
        drop:
+         - ALL
```

## Why does this exist? (Root Cause)

Allowed capabilities beyond the default set pose a high security risk.

## Affected Components

Containers and initContainers

## Additional Resources

For more details, please refer to the [official Kubernetes documentation.](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/#set-capabilities-for-a-container)