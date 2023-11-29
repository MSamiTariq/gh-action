---
title: RBAC resources v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `rbac.authorization.k8s.io/v1` API version, available since `v1.8`.  
All existing persisted objects are accessible via the new APIs  
No notable changes

```yaml sample-pod
- apiVersion: rbac.authorization.k8s.io/v1beta1
+ apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: default
  name: test
rules:
- apiGroups: ["*"]
  resources: ["*"]
  verbs: ["*"]
```

For more details on the deprecation of ClusterRole, ClusterRoleBinding, Role, and RoleBinding, please refer to the official Kubernetes documentation here:  [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `rbac.authorization.k8s.io/v1beta1` API version of ClusterRole, ClusterRoleBinding, Role, and RoleBinding is no longer served as of `v1.22`.

## Additional resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#rbac-resources-v122)