---
title: DaemonSet v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `apps/v1` API version, available since `v1.9`.  
All existing persisted objects are accessible via the new API  
Notable changes:

- `spec.templateGeneration` is removed
- `spec.selector` is now required and immutable after creation; use the existing template labels as the selector for seamless upgrades
- `spec.updateStrategy.type` now defaults to `RollingUpdate` (the default in extensions/v1beta1 was `OnDelete`) 

```yaml sample-daemonset.yaml
- apiVersion: apps/v1beta2
+ apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: test
spec:
  selector:
    matchLabels:
      name: test
  template:
    metadata:
      labels:
        name: test
    spec:
      serviceAccountName: test
      initContainers:
      - name: test-1
        image: docker/test
  updateStrategy:
    type: OnDelete
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `extensions/v1beta1` and `apps/v1beta2` API versions of DaemonSet are no longer served as of `v1.16`.

## Additional Resources

For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#daemonset-v116)