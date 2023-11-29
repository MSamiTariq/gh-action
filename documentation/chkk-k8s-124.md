---
title: CSIStorageCapacity v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `storage.k8s.io/v1` API version, available since `v1.24`.  
All existing persisted objects are accessible via the new API  
No notable changes

```yaml sample-statefulset.yaml
+ apiVersion: storage.k8s.io/v1
- apiVersion: storage.k8s.io/v1beta1
kind: CSIStorageCapacity
metadata: (ObjectMeta)
```

For more details on the deprecation of StatefulSet, please refer to the official Kubernetes documentation here:  [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `storage.k8s.io/v1beta1` API version of CSIStorageCapacity will no longer be served in `v1.27`.

## Additional Resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#csistoragecapacity-v127)