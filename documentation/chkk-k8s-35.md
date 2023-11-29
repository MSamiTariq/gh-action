---
title: Do not specify hostPort for Containers unless strictly required
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Do not specify hostPort for a Pod unless it is strictly necessary.

```yaml sample-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: frontend
spec:
  containers:
  - name: app
    image: images.my-company.example/app:v4
    ports:
-      hostPort: 8443
  - name: log-aggregator
    image: images.my-company.example/log-aggregator:v6
    ports:
-      hostPort: 5001
```

## How to fix it, short-term workaround? (Mitigation)

Avoid specifying hostPort for containers unless strictly required.

## What is the impact? (Availability Impact)

When a Pod is bound to a hostPort, it limits the number of available nodes where the Pod can be scheduled.

## Why does this exist? (Root Cause)

Since each combination of \<hostIP, hostPort, protocol> is always required to be unique, the number of available nodes where a Pod can be possibly scheduled becomes limited.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any Pod, Deployment, DaemonSet, StatefulSet, ReplicaSet, ReplicationController, Job or CronJob spec.

_Affected Images_  
All container images with hostPort specified

## Additional resources

For more details on configuring a Pods and containers, please refer to the official Kubernetes documentation here: [K8S Configuration Best Practices](https://kubernetes.io/docs/concepts/configuration/overview/)