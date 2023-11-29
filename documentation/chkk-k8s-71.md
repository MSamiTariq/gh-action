---
title: TokenReview v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `authentication.k8s.io/v1` API version, available since `v1.6`.  
No notable changes

```yaml sample-tokenreview.yaml
- apiVersion: authentication.k8s.io/v1beta1
+ apiVersion: authentication.k8s.io/v1
kind: TokenReview
metadata:
  name: "sample"
spec:
  audiences:
  - "sample1"
  token: "20"
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `authentication.k8s.io/v1beta1` API version of TokenReview is no longer served as of `v1.22`.

## Additional resources

For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#tokenreview-v122)