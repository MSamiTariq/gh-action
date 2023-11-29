---
title: PodSecurityPolicy should not allow root containers
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Run container with rule MustRunAsNonRoot.

```yaml
apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: <policy name>
spec:
    runAsUser:
+   rule: 'MustRunAsNonRoot'
or
    rule: 'MustRunAs'
    ranges:
+   - min: <min user, 1 or higher>
      max: <max user>
```

## Why does this exist? (Root Cause)

Root containers effectively have privileged access to the underlying host, thereby increasing the risk of exploit by an unauthorized process running in such a container.

## Affected Components

PodSecurityPolicy

## Additional Resources

For more details, please refer to the [official Kubernetes documentation.](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/)