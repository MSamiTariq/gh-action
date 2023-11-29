---
title: IngressClass v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `networking.k8s.io/v1` API version, available since `v1.19`.  
All existing persisted objects are accessible via the new API  
No notable changes

```yaml sample-ingressclass.yaml
- apiVersion: networking.k8s.io/v1beta1
+ apiVersion: networking.k8s.io/v1
kind: IngressClass
metadata:
  name: nginx
spec:
  controller: nginx.org/ingress-controller
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `networking.k8s.io/v1beta1` API version of IngressClass is no longer served as of `v1.22`.

## Additional resources

For more details on the deprecation of `networking.k8s.io/v1beta1` API version of IngressClass, please refer to the official Kubernetes documentation here: [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#ingressclass-v122)