---
title: Lease v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `coordination.k8s.io/v1` API version, available since `v1.14`.  
All existing persisted objects are accessible via the new API  
No notable changes

```yaml sample-lease.yaml
- apiVersion: coordination.k8s.io/v1beta1
+ apiVersion: coordination.k8s.io/v1
kind: Lease
metadata:
  name: "2"
spec:
  holderIdentity: "24"
  leaseDurationSeconds: -1978186127
  leaseTransitions: -1821918122
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `coordination.k8s.io/v1beta1` API version of Lease is no longer served as of `v1.22`.

## Additional Resources

For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#lease-v122)