---
title: PodDisruptionBudget v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `policy/v1` API version, available since `v1.21`.  
All existing persisted objects are accessible via the new API  
Notable changes in `policy/v1`:

- an empty `spec.selector ({})` written to a `policy/v1` PodDisruptionBudget selects all pods in the namespace (in `policy/v1beta1` an empty `spec.selector` selected no pods). An unset `spec.selector` selects no pods in either API version 

```yaml sample-poddisruptionbudget.yaml
- apiVersion: policy/v1beta1
+ apiVersion: policy/v1
kind: PodDisruptionBudget
metadata:
  name: zookeeper
  labels:
    app: zookeeper
    component: server
spec:
  selector:
    matchLabels:
      app: zookeeper
      component: server
  maxUnavailable: 1
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `policy/v1beta1` API version of PodDisruptionBudget will no longer be served in `v1.25`.

## Additional resources

For more details on the deprecation of PodDisruptionBudget, please refer to the official Kubernetes documentation here: [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#poddisruptionbudget-v125)