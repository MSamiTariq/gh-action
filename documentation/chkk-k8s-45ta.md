---
title: SecurityContext should be configured for pods and containers
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Configure securityContext to define explicit privilege and permissions for pods and containers.

```yaml Pod
apiVersion: v1
kind: Pod
metadata:
  name: <name>
spec:
+  securityContext:
```
```yaml Container
apiVersion: v1
kind: Pod
metadata:
  name: <Pod name>
spec:
  containers:
  - name: app
    image: images.my-company.example/app:v4
+   securityContext:
```
```yaml CronJob
apiVersion: batch/v1beta1
kind: CronJob
metadata:
  name: <name>
spec:
  schedule: <>
  jobTemplate:
    spec:
      template:
        spec:
+          securityContext:
```

## Why does this exist? (Root Cause)

Undefined security context violates the principle of least privilege by allowing container processes to perform unauthorized and insecure actions.

## Affected Components

Pod, Deployment, DaemonSet, StatefulSet, ReplicaSet, ReplicationController, Job and CronJob

## Additional Resources

For more details, please refer to the [official Kubernetes documentation.](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/)