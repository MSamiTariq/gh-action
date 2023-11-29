---
title: Containers should run as a high UID to avoid host conflict
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Container processes should be run as users with `runAsUser` > 10000.

```yaml Pod
apiVersion: v1
kind: Pod
metadata:
  name: <name>
spec:
    securityContext:
+   runAsUser: <UID higher then 10000>
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
          securityContext:
+           runAsUser: <UID higher then 1000>
```

## How to fix it, short-term workaround? (Mitigation)

Container processes should be run as users with `runAsUser` > 10000.

## What is the impact? (Availability Impact)

Container processes running with low UID can conflict with privileged processes running on the host.

## Why does this exist? (Root Cause)

To avoid the possibility of granting elevated host privileges to processes, a high User ID should be assigned to the containers.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any Pod, Deployment, DaemonSet, StatefulSet, ReplicaSet, ReplicationController, Job or CronJob spec.

_Affected Images_  
All container images with `imagePullPolicy` set to `Always`

## Additional Resources

For more details, please refer to the [official Kubernetes documentation.](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/#set-the-security-context-for-a-pod)