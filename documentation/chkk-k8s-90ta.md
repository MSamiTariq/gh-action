---
title: Webhook resources matchPolicy default change
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Define the `matchPolicy` for each webhook if you want a different value

```yaml sample-webhook.yaml
apiVersion: admissionregistration.k8s.io/v1beta1
kind: MutatingWebhookConfiguration
webhooks:
- clientConfig:
    caBundle: Cg==
    service:
      name: test
      path: /test
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
  timeoutSeconds: 30
  + matchPolicy: Equivalent
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

In Kubernetes `v1.22`, the webhook resources `webhooks[*].matchPolicy` default value was changed from `Exact` to `Equivalent`  in `admissionregistration.k8s.io/v1`.

## Additional Resources

For more information, see:

1. [official Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#webhook-resources-v122).
2. [Matching requests: matchPolicy](https://kubernetes.io/docs/reference/access-authn-authz/extensible-admission-controllers/#matching-requests-matchpolicy)