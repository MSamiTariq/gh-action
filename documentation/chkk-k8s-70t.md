---
title: SubjectAccessReview resources v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

[block:api-header]
{
  "title": "How to fix it, long-term fix? (Remediation)"
}
[/block]
Migrate manifests and API clients to use the `authorization.k8s.io/v1` API version, available since `v1.6`.
Notable changes:
  * `spec.group` was renamed to `spec.groups` in v1 
[block:code]
{
  "codes": [
    {
      "code": "- apiVersion: authorization.k8s.io/v1beta1\n+ apiVersion: authorization.k8s.io/v1\nkind: LocalSubjectAccessReview\nmetadata:\n  name: \"2\"\n  namespace: \"4\"\n  resourceVersion: \"16964250748386560239\"\n  selfLink: \"5\"\nspec:\n  extra:\n    \"35\":\n    - \"36\"\n  group:\n  - \"34\"\n  nonResourceAttributes:\n    path: \"31\"\n    verb: \"32\"\n  resourceAttributes:\n    group: \"26\"\n    name: \"30\"\n    namespace: \"24\"\n    resource: \"28\"\n    subresource: \"29\"\n    verb: \"25\"\n    version: \"27\"\n  uid: \"37\"\n  user: \"33\"\nstatus:\n  allowed: false\n  denied: true\n  evaluationError: \"39\"\n  reason: \"38\"\n",
      "language": "yaml",
      "name": "sample.yaml"
    }
  ]
}
[/block]

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
The authorization.k8s.io/v1beta1 API version of LocalSubjectAccessReview, SelfSubjectAccessReview, SubjectAccessReview, and SelfSubjectRulesReview is no longer served as of `v1.22`.
[block:api-header]
{
  "title": "Additional Resources"
}
[/block]
For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#subjectaccessreview-resources-v122)