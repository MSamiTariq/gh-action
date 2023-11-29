---
title: Do not admit Privileged Containers
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Set `privileged` to `false` in the PodSecurityPolicy (PSP)

```yaml sample-pod-security-policy.yaml
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
+  privileged: false
```

## What is the impact? (Availability Impact)

If a privileged container is compromised, an attacker will be able to run full host root with all of the available capabilities, including `CAP_SYS_ADMIN`

## Affected Components

PodSecurityPolicy

## Additional Resources

For more details on configuring security policies for Pods, please refer to the [official Kubernetes documentation.](https://kubernetes.io/docs/concepts/policy/pod-security-policy/)