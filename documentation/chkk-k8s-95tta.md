---
title: CustomResourceDefinition spec.validation renamed
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Define `spec.versions[*].schema` instead.

```yaml sample-crd.yaml
apiVersion: apiextensions.k8s.io/v1beta1
kind: CustomResourceDefinition
spec:
  group: test.group
  version: v1
  scope: Namespaced
  - validation:
  + schema:
    openAPIV3Schema:
      description: test
      properties:
        apiVersion:
          description: test
          type: string
        kind:
          description: test
          type: string
        spec:
          description: test
```

For more details on the deprecation of Ingress, please refer to the official Kubernetes documentation here: [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

CustomResourceDefinition `spec.validation` has been renamed in `apiextensions.k8s.io/v1`.

## Additional Resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#customresourcedefinition-v122)