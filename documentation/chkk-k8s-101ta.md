---
title: SubjectAccessReview resources spec.group renamed
category: 655c49ff76fdad0024723139
---

[block:api-header]
{
  "title": "How to fix it, long-term fix? (Remediation)"
}
[/block]
After upgrade, change to `spec.groups`
[block:code]
{
  "codes": [
    {
      "code": "apiVersion: authorization.k8s.io/v1beta1\nkind: SubjectAccessReview\nspec:\n  - group:\n  + groups:\n  - \"34\"\n  resourceAttributes:\n    group: \"26\"\n    name: \"30\"\n  uid: \"37\"\n  user: \"33\"\nstatus:\n  allowed: false\n  denied: true\n  evaluationError: \"39\"\n  reason: \"38\"\n",
      "language": "yaml",
      "name": "sample-sar.yaml"
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
SubjectAccessReview resources `spec.group` property has been renamed in `authorization.k8s.io/v1`.
[block:api-header]
{
  "title": "Additional Resources"
}
[/block]
For more details, please refer to the [official Kubernetes documentation ](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#subjectaccessreview-resources-v122)