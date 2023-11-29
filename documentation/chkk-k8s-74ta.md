---
title: Deployment v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `apps/v1` API version, available since `v1.9`.  
All existing persisted objects are accessible via the new API  
Notable changes:

- `spec.rollbackTo` is removed
- `spec.selector` is now required and immutable after creation; use the existing template labels as the selector for seamless upgrades
- `spec.progressDeadlineSeconds` now defaults to `600 seconds` (the default in `extensions/v1beta1` was no deadline)
- `spec.revisionHistoryLimit now defaults to `10 (the default in `apps/v1beta1` was 2, the default in `extensions/v1beta1` was to retain all)
- `maxSurge` and `maxUnavailable` now default to `25%` (the default in `extensions/v1beta1` was `1`) 

```yaml sample-deployment.yaml
- apiVersion: extensions/v1beta1
+ apiVersion: apps/v1
kind: Deployment
metadata:
  name: helloweb
  labels:
    app: hello
spec:
  selector:
    matchLabels:
      app: hello
      tier: web
  template:
    metadata:
      labels:
        app: hello
        tier: web
    spec:
      containers:
      - name: hello-app
        image: test/test
        ports:
        - containerPort: 8080
        resources:
          requests:
            cpu: 200m
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `extensions/v1beta1`, `apps/v1beta1`, and `apps/v1beta2` API versions of Deployment are no longer served as of v1.16.

## Additional Resources

For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#deployment-v116)