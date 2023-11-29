---
title: PodSecurityPolicy should configure seccomp profile as docker/default or runtime/default
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

PodSecurityPolicy should configure seccomp profile to `docker/default` or `runtime/default`.

```yaml
apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: restricted
  annotations:
    seccomp.security.alpha.kubernetes.io/allowedProfileNames: 'docker/default,runtime/default'
    apparmor.security.beta.kubernetes.io/allowedProfileNames: 'runtime/default'
    seccomp.security.alpha.kubernetes.io/defaultProfileName:  'runtime/default'
    apparmor.security.beta.kubernetes.io/defaultProfileName:  'runtime/default'
```

## Why does this exist? (Root Cause)

An undefined seccomp profile can lead to a container process making unrestricted and unauthorized system calls.

## Affected Components

PodSecurityPolicy

## Additional Resources

For more details refer to [official documentation]<https://kubernetes.io/docs/tutorials/security/seccomp/>)