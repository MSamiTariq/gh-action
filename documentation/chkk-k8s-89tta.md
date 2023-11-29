---
title: Webhook resources failurePolicy default change
category: 655c49ff76fdad0024723139
---

[block:api-header]
{
  "title": "How to fix it, long-term fix? (Remediation)"
}
[/block]
Define the `failurePolicy` for each webhook if you want a different value
[block:code]
{
  "codes": [
    {
      "code": "apiVersion: admissionregistration.k8s.io/v1beta1\nkind: MutatingWebhookConfiguration\nwebhooks:\n- clientConfig:\n    caBundle: Cg==\n    service:\n      name: test\n      path: /test\n  matchPolicy: Equivalent\n  name: test.name\n  rules:\n  - apiGroups:\n    - \"\"\n    apiVersions:\n    - v1\n    operations:\n    - CREATE\n    - UPDATE\n    resources:\n    - replicationcontrollers\n  sideEffects: None\n  timeoutSeconds: 30\n  + failurePolicy: Ignore\n\n",
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
Webhook resources `webhooks[*].failurePolicy` default value has been changed from `Ignore` to `Fail`  in `admissionregistration.k8s.io/v1`.
[block:api-header]
{
  "title": "Additional Resources"
}
[/block]

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#webhook-resources-v12)