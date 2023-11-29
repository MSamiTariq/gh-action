---
title: ReplicaSet v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the  `apps/v1` API version, available since `v1.9`.  
All existing persisted objects are accessible via the new API  
Notable changes:

- `spec.selector` is now required and immutable after creation; use the existing template labels as the selector for seamless upgrades 

```yaml sample-replicaset.yaml
- apiVersion: extensions/v1beta1
+ apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: test
spec:
  replicas: 3
  selector:
    matchLabels:
      app: test
      tier: frontend
  template:
    metadata:
      labels:
        app: guestbook
        tier: frontend
    spec:
      containers:
      - name: test
        image: test/test
        resources:
          requests:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
```

For more details on the deprecation of ReplicaSet, please refer to the official Kubernetes documentation here:  [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `extensions/v1beta1`, `apps/v1beta1`, and `apps/v1beta2` API versions of ReplicaSet are no longer served as of `v1.16`.

## Additional resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#replicaset-v11)