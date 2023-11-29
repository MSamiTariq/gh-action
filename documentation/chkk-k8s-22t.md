---
title: PodSecurityPolicy should be configured to restrict assigning additional capabilities to containers
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Configure PodSecurityPolicy to assign containers with limited capabilities.

```yaml
apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: <policy name>
spec:
- allowedCapabilities:
```

## Why does this exist? (Root Cause)

In general, containers should not be assigned capabilities beyond the default set. This poses a high security risk as it provides containers with privileges that are traditionally associated with the superuser.

## Affected Components

PodSecurityPolicy

## Additional Resources

For more details, please refer to the official [Kubernetes Documentation](https://kubernetes.io/docs/concepts/policy/pod-security-policy/).