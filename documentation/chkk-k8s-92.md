---
title: Webhook resources sideEffects default removed
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Define the `sideEffects` for each webhook to `None` or `NoneOnDryRun`

```yaml sample-webhook.yaml
apiVersion: admissionregistration.k8s.io/v1
kind: MutatingWebhookConfiguration
webhooks:
- clientConfig:
    caBundle: Cg==
    service:
      name: test
      path: /test
  matchPolicy: Equivalent
  name: test.name
  rules:
  - apiGroups:
    - ""
    apiVersions:
    - v1
    operations:
    - CREATE
    - UPDATE
    resources:
    - replicationcontrollers
  timeoutSeconds: 30
  + sideEffects: None
```

For more details on the deprecation of Ingress, please refer to the official Kubernetes documentation here:  [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

Webhook resources `webhooks[*].sideEffects` default value has been removed in `admissionregistration.k8s.io/v1`.

## Additional Resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#webhook-resources-v12)