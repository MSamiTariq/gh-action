---
title: StatefulSet v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the apps/v1 API version, available since `v1.19`.  
All existing persisted objects are accessible via the new API  
Notable changes:

- `spec.selector` is now required and immutable after creation; use the existing template labels as the selector for seamless upgrades
- `spec.updateStrategy.type` now defaults to `RollingUpdate` (the default in `apps/v1beta1` was `OnDelete`) 

```yaml sample-statefulset.yaml
- apiVersion: apps/v1beta1
+ apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: test
spec:
  serviceName: "nginx"
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: k8s.gcr.io/nginx-slim:0.8
        ports:
        - containerPort: 80
          name: web
        volumeMounts:
        - name: www
          mountPath: /usr/share/nginx/html
```

For more details on the deprecation of StatefulSet, please refer to the official Kubernetes documentation here:  [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `apps/v1beta1` and `apps/v1beta2` API versions of StatefulSet are no longer served as of `v1.16`.

## Additional Resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#statefulset-v116)