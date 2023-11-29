---
title: RuntimeClass v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `node.k8s.io/v1` API version, available since `v1.20`.  
All existing persisted objects are accessible via the new API  
No notable changes

```yaml sample-statefulset.yaml
- apiVersion: node.k8s.io/v1beta1
+ apiVersion: node.k8s.io/v1
kind: RuntimeClass
metadata:
  name: myclass 
# The name of the corresponding CRI configuration
handler: myconfiguration
```

For more details on the deprecation of StatefulSet, please refer to the official Kubernetes documentation here:  [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

RuntimeClass in the `node.k8s.io/v1beta1` API version will no longer be served in `v1.25`.

## Additional Resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#runtimeclass-v125)