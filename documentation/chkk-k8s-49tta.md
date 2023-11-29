---
title: Prefer using read-only filesystem in containers
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Set `readOnlyRootFilesystem` to true to define read-only permissions for mounted filesystem.

```yaml sample-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: <Pod name>
spec:
  containers:
  - name: <container name>
    image: <image>
    securityContext:
+      readOnlyRootFilesystem: true
```

## How to fix it, short-term workaround? (Mitigation)

Set `readOnlyRootFilesystem` to true to define read-only permissions for mounted filesystem.

## What is the impact? (Availability Impact)

Filesystems mounted with undefined permissions can allow a malicious process to write to the host system.

## Why does this exist? (Root Cause)

By default, a container is allowed to write to the root filesystem. This violates the principle of least privilege and increases the risk of exploiting the host system.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any Pod, Deployment, DaemonSet, StatefulSet, ReplicaSet, ReplicationController, Job or CronJob spec.

_Affected Images_  
All container images with `readOnlyRootFilesystem` set to False.

## Additional Resources

For more details, please refer to the [Security Best Practices](https://kubernetes.io/blog/2016/08/security-best-practices-kubernetes-deployment/)