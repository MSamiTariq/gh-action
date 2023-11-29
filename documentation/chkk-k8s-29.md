---
title: Avoid using the default namespace
category: 655c49ff76fdad0024723139
---

[block:api-header]
{
  "title": "How to fix it, long-term fix? (Remediation)"
}
[/block]
Create a new namespace for your application and deploy it in the namespace (i.e. not default)
[block:code]
{
  "codes": [
    {
      "code": "apiVersion: v1\nkind: Pod\nmetadata:\n  name: frontend\n+ namespace: tenant1\nspec:\n  containers:\n  - name: app\n    image: images.my-company.example/app:v4\n    resources:\n      requests:\n        memory: \"64Mi\"\n        cpu: \"250m\"\n      limits:  # Define resource limits for container\n        memory: \"128Mi\" # Set memory limit\n        cpu: \"500m\" # Set CPU limit\n  - name: log-aggregator\n    image: images.my-company.example/log-aggregator:v6\n    resources:\n      requests:\n        memory: \"64Mi\"\n        cpu: \"250m\"\n      limits: # Define resource limits for container\n        memory: \"128Mi\" # Set memory limit\n        cpu: \"500m\" # Set CPU limit",
      "language": "yaml",
      "name": "sample-pod.yaml"
    },
    {
      "code": "# coming soon",
      "language": "yaml",
      "name": "Terraform"
    },
    {
      "code": "# coming soon",
      "language": "yaml"
    }
  ]
}
[/block]

[block:api-header]
{
  "title": "How to fix it, short-term workaround? (Mitigation)"
}
[/block]
There is no mitigation or workaround for this Availability Risk Signature.
[block:api-header]
{
  "title": "Why does this exist? (Root Cause)"
}
[/block]
Anything running in production in default namespace is an accident waiting to happen. Most of the Kubernetes tooling creates resources in the default namespace if namespace is not specified, often leading to undesired behavior. Default namespace is where pilot errors happen the most.

[block:callout]
{
  "type": "info",
  "title": "Note",
  "body": "If the namespace is not explicitly set, the object is automatically deployed in the default namespace."
}
[/block]

[block:api-header]
{
  "title": "Who is impacted and when? (Trigger Conditions)"
}
[/block]
  * Pod, Deployment, DaemonSet, StatefulSet, ReplicaSet, ReplicationController, Job and CronJob
[block:api-header]
{
  "title": "Additional Resources"
}
[/block]
For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/).