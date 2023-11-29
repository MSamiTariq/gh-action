---
title: Storage resources v1beta1/VolumeAttachment Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `storage.k8s.io/v1` API version

- `VolumeAttachment` is available in `storage.k8s.io/v1` `v1.13`

All existing persisted objects are accessible via the new APIs  
No notable changes

```yaml sample-csinode.yaml
- apiVersion: storage.k8s.io/v1beta1
+ apiVersion: storage.k8s.io/v1
kind: VolumeAttachment
metadata:
  name: test
spec:
  drivers:
  - name: "24"
    nodeID: "25"
    topologyKeys:
    - "26"
```

For more details on the deprecation of CSIDriver, CSINode, StorageClass, and VolumeAttachment, please refer to the official Kubernetes documentation here:  [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The storage.k8s.io/v1beta1 API version of `CSIDriver`, `CSINode`, `StorageClass`, and `VolumeAttachment` is no longer served as of `v1.22`.

## Additional Resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#storage-resources-v122)