---
title: PodSecurityPolicy should not allow containers to share the host IPC namespace
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

PodSecurityPolicy should disable hostIPC to restrict Pods from communicating with host processes via IPC.

```yaml
apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: <policy name>
spec:
+ hostIPC: false
```

## How to fix it, short-term workaround? (Mitigation)

Define PodSecurityPolicy to disable hostIPC communication.

## What is the impact? (Availability Impact)

By sharing the host process IPC namespace, process isolation between containers in a Pod and the host is compromised. This allows a process to communicate with host processes via IPC.

## Why does this exist? (Root Cause)

In general container processes should not be allowed to communicate with other processes running outside that container. To cater for exceptional scenarios, a separate PodSecurityPolicy should be defined with limited RBAC policies.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any Pod, Deployment, DaemonSet, StatefulSet, ReplicaSet, ReplicationController, Job or CronJob spec.

_Affected Images_  
All container images with `hostIPC` set to `true`.

## Additional resources

For more details, please refer to the official [kubernetes documentation](https://kubernetes.io/docs/concepts/security/pod-security-policy/)