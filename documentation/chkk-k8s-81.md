---
title: PodSecurityPolicy v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API client to use the `policy/v1beta1` API version, available since `v1.10`.  
Note that the `policy/v1beta1` API version of PodSecurityPolicy will be removed in `v1.25`.

```yaml sample-podsecuritypolicy.yaml
-apiVersion: extensions/v1beta1
+apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: test
spec:
  fsGroup:
    rule: RunAsAny
  privileged: true
  runAsUser:
    rule: RunAsAny
  seLinux:
    rule: RunAsAny
  supplementalGroups:
    rule: RunAsAny
  volumes:
  - '*'
  allowedCapabilities:
  - '*'
  hostPID: true
  hostIPC: true
  hostNetwork: true
  hostPorts:
  - min: 1
    max: 65536
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `extensions/v1beta1` API version of PodSecurityPolicy is no longer served as of `v1.16`.

## Additional Resources

For more details on the deprecation of PodSecurityPolicy, please refer to the official Kubernetes documentation here: [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#psp-v116)