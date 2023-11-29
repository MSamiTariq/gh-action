---
title: Configure Liveness probes for Containers
category: 655c49ff76fdad0024723139
---

Severity: Low

## How to fix it, long-term fix? (Remediation)

Define the Liveness probes at `.spec.containers[].livenessProbe` for each container.

```yaml sample-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  labels:
    test: liveness
  name: liveness-exec
spec:
  containers:
  - name: liveness
    image: k8s.gcr.io/busybox
    args:
    - /bin/sh
    - -c
    - touch /tmp/healthy; sleep 30; rm -rf /tmp/healthy; sleep 600
+   livenessProbe:
+     exec:
+       command:
+       - cat
+       - /tmp/healthy
+     initialDelaySeconds: 5
+     periodSeconds: 5
```

## How to fix it, short-term workaround? (Mitigation)

Define the Liveness probes at `.spec.containers[].livenessProbe` for each container.

## What is the impact? (Availability Impact)

With out liveness probes in place, applications lose the ability to recover from unexpected deadlocks and race conditions, impacting their overall availability.

## Why does this exist? (Root Cause)

Application are not without bugs. Liveness probes help catch a deadlock, where an application is running, but unable to make progress. Restarting a container in such a state can help to make the application more available despite bugs.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes versions.

_Affected Images_  
All Pods, Deployments, Daemonsets including containers and initContainers are affected by this.

## Additional Resources

For more details on configuring Liveness probes for containers, please refer to the official Kubernetes documentation here: [K8S Configure Liveness Readiness and Startup Probes](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/)