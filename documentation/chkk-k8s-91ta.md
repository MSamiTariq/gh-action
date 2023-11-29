---
title: Webhook resources timeoutSeconds default change
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Define the `timeoutSeconds` for each webhook if you want a different value

```yaml sample-webhook.yaml
apiVersion: admissionregistration.k8s.io/v1beta1
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
  sideEffects: None
  + timeoutSeconds: 30
```

For more details on the deprecation of Ingress, please refer to the official Kubernetes documentation here: [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

Webhook resources `webhooks[*].timeoutSeconds` default value has been changed from `30s` to `10s`  in `admissionregistration.k8s.io/v1`.

## Additional Resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#webhook-resources-v12)