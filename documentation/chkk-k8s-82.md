---
title: PriorityClass v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `scheduling.k8s.io/v1` API version, available since `v1.14`.  
All existing persisted objects are accessible via the new API  
No notable changes

```yaml sample-priorityclass.yaml
- apiVersion: scheduling.k8s.io/v1beta1
+ apiVersion: scheduling.k8s.io/v1
kind: PriorityClass
metadata:
  name: test
value: "23"
globalDefault: false
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `scheduling.k8s.io/v1beta1` API version of PriorityClass is no longer served as of `v1.22`.

## Additional Resources

For more details on the deprecation of PriorityClass, please refer to the official Kubernetes documentation here:  [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#priorityclass-v122)