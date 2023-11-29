---
title: HorizontalPodAutoscaler v2beta2 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `autoscaling/v2` API version, available since `v1.23`.  
All existing persisted objects are accessible via the new API

```yaml sample-podautoscaler.yaml
+ apiVersion: autoscaling/v2
- apiVersion: autoscaling/v2beta2
kind: HorizontalPodAutoscaler
metadata:
  name: test
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: php-apache
  minReplicas: 1
  maxReplicas: 10
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 50
```

For more details on the deprecation of StatefulSet, please refer to the official Kubernetes documentation here:  [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `autoscaling/v2beta2` API version of HorizontalPodAutoscaler will no longer be served in `v1.26`.

## Additional Resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#horizontalpodautoscaler-v126)