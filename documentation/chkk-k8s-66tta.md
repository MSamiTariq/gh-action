---
title: APIService v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `apiregistration.k8s.io/v1` API version, available since `v1.10`.  
All existing persisted objects are accessible via the new API  
No notable changes

```yaml sample-apiservice.yaml
- apiVersion: apiregistration.k8s.io/v1beta1
+ apiVersion: apiregistration.k8s.io/v1
kind: APIService
metadata:
  name: v1beta1.custom.metrics.k8s.io
spec:
  service:
    name: custom-metrics-apiserver
    namespace: custom-metrics
  group: custom.metrics.k8s.io
  version: v1beta1
  insecureSkipTLSVerify: true
  groupPriorityMinimum: 100
  versionPriority: 100
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `apiregistration.k8s.io/v1beta1` API version of APIService is no longer served as of `v1.22.`

## Additional Resources

For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#apiservice-v122).