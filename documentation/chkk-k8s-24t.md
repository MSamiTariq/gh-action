---
title: Containers should not run with allowPrivilegeEscalation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Ensure that the `.spec.allowPrivilegeEscalation` field is set to `false`. Default is `true`.

```yaml sample-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: frontend
spec:
  containers:
  - name: app
    image: images.my-company.example/app:v4
    securityContext:
+      allowPrivilegeEscalation: false
  - name: log-aggregator
    image: images.my-company.example/log-aggregator:v6
    securityContext:
+      allowPrivilegeEscalation: false
```

## Why does this exist? (Root Cause)

A container running with the allowPrivilegeEscalation flag set to true may have processes that can gain more privileges than their parent.

## Affected Components

Containers and initContainers

## Additional Resources

For more details, please refer to the original [Kubernetes Documentation](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/)