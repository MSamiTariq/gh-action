---
title: CustomResourceDefinition v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `apiextensions.k8s.io/v1` API version, available since `v1.16`.  
All existing persisted objects are accessible via the new API  
Notable changes:

- `spec.scope` is no longer defaulted to `Namespaced` and must be explicitly specified
- `spec.version` is removed in v1; use `spec.versions` instead
- `spec.validation` is removed in v1; use `spec.versions[*].schema` instead
- `spec.subresources` is removed in v1; use `spec.versions[*].subresources` instead
- `spec.additionalPrinterColumns` is removed in v1; use `spec.versions[*].additionalPrinterColumns` instead
- `spec.conversion.webhookClientConfig` is moved to `spec.conversion.webhook.clientConfig` in v1
- `spec.conversion.conversionReviewVersions` is moved to `spec.conversion.webhook.conversionReviewVersions` in v1
- `spec.versions[*].schema.openAPIV3Schema` is now required when creating v1 `CustomResourceDefinition` objects, and must be a structural schema
- `spec.preserveUnknownFields:` true is disallowed when creating v1 `CustomResourceDefinition` objects; it must be specified within schema definitions as `x-kubernetes-preserve-unknown-fields: true`
- In `additionalPrinterColumns` items, the `JSONPath` field was renamed to `jsonPath` in v1 

```yaml sample-customresourcedefinition.yaml
- apiVersion: "apiextensions.k8s.io/v1beta1"
+ apiVersion: "apiextensions.k8s.io/v1"
kind: "CustomResourceDefinition"
metadata:
  name: sample-project
spec:
  group: "example.sample-project"
  version: "v1alpha1"
  scope: "Namespaced"
  names:
    plural: "projects"
    singular: "project"
    kind: "Project"
  validation:
    openAPIV3Schema:
      required: ["spec"]
      properties:
        spec:
          required: ["replicas"]
          properties:
            replicas:
              type: "integer"
              minimum: 1
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `apiextensions.k8s.io/v1beta1` API version of CustomResourceDefinition is no longer served as of `v1.22`.

## Additional Resources

For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#customresourcedefinition-v122)