---
title: Webhook resources v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `admissionregistration.k8s.io/v1` API version, available since `v1.16`.  
All existing persisted objects are accessible via the new APIs  
Notable changes:

- `webhooks[*].failurePolicy` default changed from `Ignore` to `Fail` for v1
- `webhooks[*].matchPolicy` default changed from `Exact` to `Equivalent` for v1
- `webhooks[*].timeoutSeconds` default changed from `30s` to `10s` for v1
- `webhooks[*].sideEffects` default value is removed, and the field made required, and only `None` and `NoneOnDryRun` are permitted for v1
- `webhooks[*].admissionReviewVersions` default value is removed and the field made required for v1 (supported versions for AdmissionReview are` v1` and `v1beta1`)
- `webhooks[*].name` must be unique in the list for objects created via `admissionregistration.k8s.io/v1`

```yaml sample-mutatingwebhookconfiguration.yaml
- apiVersion: admissionregistration.k8s.io/v1beta1
+ apiVersion: admissionregistration.k8s.io/v1
kind: MutatingWebhookConfiguration
metadata:
  name: Test
webhooks:
  - name: test.helloworld.com
    clientConfig:
      service:
        name: test
        namespace: helloworld
        path: /test/
    rules:
      - operations: ["CREATE", "UPDATE"]
        resources:
          - services
    failurePolicy: Fail
```

For more details on the deprecation of MutatingWebhookConfiguration and ValidatingWebhookConfiguration, please refer to the official Kubernetes documentation here:  
 [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `admissionregistration.k8s.io/v1beta1` API version of MutatingWebhookConfiguration and ValidatingWebhookConfiguration is no longer served as of `v1.22`.

## Additional resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#webhook-resources-v122)