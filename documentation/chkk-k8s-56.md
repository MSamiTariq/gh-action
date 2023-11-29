---
title: Do not use Service Account Tokens unless strictly required
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Set `automountServiceAccountToken` to false in the Pod or ServiceAccount.

```yaml Pod
apiVersion: v1
kind: Pod
metadata:
  name: test
spec:
+  automountServiceAccountToken: false
```
```yaml CronJob
apiVersion: batch/v1beta1
kind: CronJob
metadata:
  name: test
spec:
  schedule: <>
  jobTemplate:
    spec:
      template:
        spec:
+         automountServiceAccountToken: false
```

## Why does this exist? (Root Cause)

If the authentication token for a privileged Service Account is compromised, a malicious process can then access the Kubernetes API Server and perform wide ranging exploits.

## Affected Components

Pod, Deployment, DaemonSet, StatefulSet, ReplicaSet, ReplicationController, Job, CronJob and ServiceAccount.

## Additional resources

For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/)