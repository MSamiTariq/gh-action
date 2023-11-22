---
title: PodSecurityPolicy should restrict running Containers with allowPrivilegeEscalation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Create a PSP as described in the Kubernetes documentation, ensuring that the `.spec.allowPrivilegeEscalation` field is omitted or set to `false`.

```yaml sample-restricted-pod-security-policy.yaml
apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: restricted
  annotations:
    seccomp.security.alpha.kubernetes.io/allowedProfileNames: 'docker/default,runtime/default'
    apparmor.security.beta.kubernetes.io/allowedProfileNames: 'runtime/default'
    seccomp.security.alpha.kubernetes.io/defaultProfileName:  'runtime/default'
    apparmor.security.beta.kubernetes.io/defaultProfileName:  'runtime/default'
spec:
  privileged: false
+  allowPrivilegeEscalation: false
  requiredDropCapabilities:
    - ALL
```

## Why does this exist? (Root Cause)

A container running with the allowPrivilegeEscalation flag set to true may have processes that can gain more privileges than their parent.

## Affected Components

Containers and initContainers

## Additional Resources

For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/)
