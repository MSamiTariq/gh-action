---
title: Containers should not share the host process ID namespace
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Remove the hostPID to restrict Pods from accessing the host PID namespace.

```yaml Pod
apiVersion: v1
kind: Pod
metadata:
  name: test
spec:
- hostPID: true
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
-          hostPID: true
```

## How to fix it, short-term workaround? (Mitigation)

Disable hostPID to restrict Pods from accessing the host PID namespace.

## What is the impact? (Availability Impact)

By sharing the host process ID namespace, process isolation between different containers in a Pod is compromised. This effectively allows a process to access sensitive information of processes running in other containers.

## Why does this exist? (Root Cause)

When sharing the host process ID namespace, every process in a container has visibility of all other processes running in the Pod. A malicious and unauthorized process can exploit this behavior to steal sensitive process information.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any Pod, Deployment, DaemonSet, StatefulSet, ReplicaSet, ReplicationController, Job or CronJob spec.

_Affected Images_  
All container images with `hostPID` set to `true`.

## Additional resources

For more details, please refer to the official [docker documentation](https://docs.docker.com/engine/reference/run/#pid-settings-pid)