---
title: Use application specific Service Accounts
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Have your application create a service account for itself with only the permissions it needs.

```yaml sample-service-account.yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: sampleSA
+ automountServiceAccountToken: false
```

Additionally, verify that any RoleBinding or ClusterRoleBinding is not bound to the default service account.

## What is the impact? (Availability Impact)

The most secure option for RBAC is to have your application create a service account for itself with only the permissions it needs. Default service account may come with permissions that your application might not need.

## Affected Components

ServiceAccount, RoleBinding and ClusterRoleBinding

## Additional Resources

For more details on using Service Accounts, please refer to the official Kubernetes documentation here: [K8S Configure Service Accounts for Pods](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/)