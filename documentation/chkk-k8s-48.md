---
title: Configure Readiness probes for containers
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Define the Readiness probes at `.spec.containers[].readinessProbe` for each container

```yaml sample-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: <name>
spec:
  containers:
  - name: <container name>
    image: <image>
+   readinessProbe:
      <Probe configurations>
```

For more details on configuring Readiness probes for containers, please refer to the official Kubernetes documentation here: [K8s-Configure-Liveness-Readiness-and-Startup-Probes](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/)

## How to fix it, short-term workaround? (Mitigation)

Configure Readiness probes to check your application business logic.

## What is the impact? (Availability Impact)

With out readiness probes in place, applications lose the ability to recover from unexpected deadlocks and race conditions, impacting their overall availability.

## Why does this exist? (Root Cause)

Application are not without bugs. Readiness probes help catch a deadlock, where an application is running, but unable to make progress. Readiness probes allows Kubelet to temporarily isolate the impacted pod from incoming traffic.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes versions.

_Affected Images_  
All Pods, Deployments, Daemonsets including containers and initContainers are affected by this.

## Additional Resources

For more details, please refer to the [official Kubernetes documentation.](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/)