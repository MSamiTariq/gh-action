---
title: Ingress v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `networking.k8s.io/v1` API version, available since `v1.19`.  
All existing persisted objects are accessible via the new API  
Notable changes:

- `spec.backend` is renamed to `spec.defaultBackend`
- The backend `serviceName` field is renamed to `service.name`
- Numeric backend `servicePort` fields are renamed to `service.port.number`
- String backend `servicePort` fields are renamed to `service.port.name`
- `pathType` is now required for each specified path. Options are `Prefix`, `Exact`, and `ImplementationSpecific`. To match the undefined `v1beta1` behavior, use `ImplementationSpecific`. 

```yaml sample-ingress.yaml
- apiVersion: extensions/v1beta1
+ apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: test
spec:
  rules:
  - host:  test.com
    http:
      paths:
      - path: /
        backend:
          serviceName: test
          servicePort: 80
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `extensions/v1beta1` and `networking.k8s.io/v1beta1` API versions of Ingress is no longer served as of `v1.22`.

## Additional resources

For more details on the deprecation of `extensions/v1beta1` and `networking.k8s.io/v1beta1` API versions of Ingress, please refer to the official Kubernetes documentation here: [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#ingress-v122)