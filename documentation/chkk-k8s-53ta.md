---
title: Set seccomp profile as docker/default or runtime/default
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Configure seccomp profile to `docker/default` or `runtime/default`.

```yaml Pod
apiVersion: v1
kind: Pod
metadata:
  name: <name>
  annotations:
+   seccomp.security.alpha.kubernetes.io/pod: "docker/default" 
    or
+   seccomp.security.alpha.kubernetes.io/pod: "runtime/default"
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
        metadata:
          annotations:
 +          seccomp.security.alpha.kubernetes.io/pod: "docker/default" 
    or
 +          seccomp.security.alpha.kubernetes.io/pod: "runtime/default"
```

## Why does this exist? (Root Cause)

Allowed capabilities beyond the default set pose a high security risk.

## Affected Components

Pod, Deployment, DaemonSet, StatefulSet, ReplicaSet, ReplicationController, Job and CronJob

## Additional Resources

For more details, please refer to the official [kubernetes documentation](https://kubernetes.io/docs/tutorials/security/seccomp/)