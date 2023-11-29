---
title: PodSecurityPolicy should not admit containers wishing to share the host network namespace
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

PodSecurityPolicy should disable hostNetwork to restrict Pods from accessing the host network namespace.

```yaml
apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: <policy name>
spec:
+ hostNetwork: false
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

For more details, please refer to the official [kubernetes documentation](https://kubernetes.io/docs/concepts/security/pod-security-policy/)