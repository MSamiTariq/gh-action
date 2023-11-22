---
title: Do not bind Role/ClusterRole to Default Service Account
category: 655c49ff76fdad0024723139
parentDocSlug: chkk-k8s-401
---

## How to fix it, long-term fix? (Remediation)

Have your application create a service account for itself with only the permissions it needs and bind that to the Role/ClusterRole.

```yaml sample-role-binding.yaml
kind: RoleBinding
apiVersion: rbac.authorization.k8s.io/v1beta1
metadata:
  name: SampleRoleBinding
  namespace: default
subjects:
  - - kind: ServiceAccount
  - name: default
  - namespace: default
roleRef:
  kind: Role
  name: SampleRole
  apiGroup: rbac.authorization.k8s.io
```

## What is the impact? (Availability Impact)

Default service account may come with permissions that your application might not need; breaking the principle of least privilege.

## Affected Components

RoleBinding and ClusterRoleBinding

## Additional Resources

For more details on using Service Accounts, please refer to the official Kubernetes documentation here: [K8S Configure Service Accounts for Pods](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/)
