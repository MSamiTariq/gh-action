---
title: PodSecurityPolicy should restrict the admission of containers with capabilities assigned
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

PodSecurityPolicy shoud assign capabilities to containers within the default set.

```yaml
apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: <policy name>
spec:
  requiredDropCapabilities: 
+   -ALL
```

## Why does this exist? (Root Cause)

Allowed capabilities beyond the default set pose a high security risk.

## Affected Components

PodSecurityPolicy

## Additional Resources

For more details, please refer to the [official Kubernetes documentation.](https://kubernetes.io/docs/concepts/security/pod-security-admission/)