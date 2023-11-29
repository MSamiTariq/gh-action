---
title: FlowControlResources v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `flowcontrol.apiserver.k8s.io/v1beta2` API version, available since `v1.23`.  
All existing persisted objects are accessible via the new API  
No notable change

```yaml sample-flowcontrol.yaml
+ apiVersion: flowcontrol.apiserver.k8s.io/v1beta2
- apiVersion: flowcontrol.apiserver.k8s.io/v1beta1
kind: FlowSchema
metadata:
  name: health-for-strangers
spec:
  matchingPrecedence: 1000
  priorityLevelConfiguration:
    name: exempt
  rules:
  - nonResourceRules:
    - nonResourceURLs:
      - "/healthz"
      - "/livez"
      verbs:
      - "*"
```

For more details on the deprecation of StatefulSet, please refer to the official Kubernetes documentation here:  [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `flowcontrol.apiserver.k8s.io/v1beta1` API version of FlowSchema and PriorityLevelConfiguration will no longer be served in `v1.26`.

## Additional Resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#flowcontrol-resources-v126)