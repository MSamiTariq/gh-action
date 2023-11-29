---
title: Containers should not share the host network namespace
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Disable hostNetwork to restrict Pods from accessing the host network namespace.

```yaml Pod
apiVersion: v1
kind: Pod
metadata:
  name: test
spec:
- hostNetwork: true
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
-          hostNetwork: true
```

## How to fix it, short-term workaround? (Mitigation)

Define a separate PodSecurityPolicy with limiting RBAC policies for containers that need to access the host network namespace.

## What is the impact? (Availability Impact)

By sharing the host network namespace, container processes can use the host networking to access and proxy network traffic between all other Pods.

## Why does this exist? (Root Cause)

In general container processes should not be allowed to access host network namespace. To cater for exceptional scenarios, a separate PodSecurityPolicy should be defined with limiting RBAC policies.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any Pod, Deployment, DaemonSet, StatefulSet, ReplicaSet, ReplicationController, Job or CronJob spec.

_Affected Images_  
All container images with `hostNetwork` set to `true`.

## Additional Resources

For more details, please visit the official [docker documentation](https://docs.docker.com/network/)