---
title: Containers should not share the host IPC namespace
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Disable hostIPC to restrict Pods from communicating with host processes via IPC.

```yaml Pod
apiVersion: v1
kind: Pod
metadata:
  name: test
spec:
- hostIPC: true
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
-          hostIPC: true
```

## How to fix it, short-term workaround? (Mitigation)

Disable hostIPC to restrict Pods from communicating with host processes via IPC.

## What is the impact? (Availability Impact)

By sharing the host process IPC namespace, process isolation between containers in a Pod and the host is compromised. This allows a process to insecurely communicate with host processes via IPC.

## Why does this exist? (Root Cause)

In general container processes should not be allowed to communicate with other processes running outside that container. To cater for exceptional scenarios, a separate PSP should be defined with limiting RBAC policies.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any Pod, Deployment, DaemonSet, StatefulSet, ReplicaSet, ReplicationController, Job or CronJob spec.

_Affected Images_  
All container images with `hostIPC` set to `true`.

## Additional Resources

For more details, please refer to the official [kubernetes documentation](https://kubernetes.io/docs/concepts/security/pod-security-policy/)