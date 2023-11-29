---
title: NetworkPolicy v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `networking.k8s.io/v1` API version, available since `v1.8`.  
All existing persisted objects are accessible via the new API

```yaml sample-networkpolicy.yaml
- apiVersion: extensions/v1beta1
+ apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: test
spec:
  podSelector:
    matchLabels:
      app: test
  policyTypes:
  - Ingress
  ingress:
  - from:
    - podSelector:
        matchLabels:
          app: www
    to:
    ports:
    - protocol: TCP
      port: 80
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `extensions/v1beta1` API version of NetworkPolicy is no longer served as of `v1.16`.

## Additional Resources

For more details on deprecation of `extensions/v1beta1` API version of NetworkPolicy, please refer to the official Kubernetes documentation here: [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#networkpolicy-v116)