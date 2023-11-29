---
title: Webhook resources admissionReviewVersions default removed
category: 655c49ff76fdad0024723139
---

[block:api-header]
{
  "title": "How to fix it, long-term fix? (Remediation)"
}
[/block]
Define the `admissionReviewVersions` for each webhook
[block:code]
{
  "codes": [
    {
      "code": "apiVersion: admissionregistration.k8s.io/v1\nkind: MutatingWebhookConfiguration\nwebhooks:\n- clientConfig:\n    caBundle: Cg==\n    service:\n      name: test\n      path: /test\n  matchPolicy: Equivalent\n  name: test.name\n  rules:\n  - apiGroups:\n    - \"\"\n    apiVersions:\n    - v1\n    operations:\n    - CREATE\n    - UPDATE\n    resources:\n    - replicationcontrollers\n  sideEffects: None\n  timeoutSeconds: 30\n\t+ admissionReviewVersions:\n  + - \"v1\"\n",
      "language": "yaml",
      "name": "sample-webhook.yaml"
    }
  ]
}
[/block]
For more details on the deprecation of Ingress, please refer to the official Kubernetes documentation here: [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/)
[block:api-header]
{
  "title": "How to fix it, short-term workaround? (Mitigation)"
}
[/block]
There is no mitigation or workaround for this Availability Risk.
[block:api-header]
{
  "title": "Why does this exist? (Root Cause)"
}
[/block]
Webhook resources `webhooks[*].admissionReviewVersions` default value has been removed in `admissionregistration.k8s.io/v1`.
[block:api-header]
{
  "title": "Additional resources"
}
[/block]
For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#webhook-resources-v12)