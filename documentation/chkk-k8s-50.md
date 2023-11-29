---
title: Restrict the deployment of Root Containers
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Run each Pod or container as a non-root user.

```yaml sample-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: security-context-demo
spec:
+ securityContext:
+   runAsNonRoot: true
+   runAsUser: 1000
  containers:
  - name: SampleNonRootContainer
    image: busybox
    command: [ "sh", "-c", "sleep 1h" ]
    volumeMounts:
    - name: sec-ctx-vol
      mountPath: /data/demo
```

## Why does this exist? (Root Cause)

Containers running as root provide elevated privileges of a root-user to all processes running inside them, thereby increasing the risk of exploit by a malicious application.

## Affected Components

Pod, Deployment, DaemonSet, StatefulSet, ReplicaSet, ReplicationController, Job and CronJob

## Additional Resources

For more details on configuring security for pods and containers, please refer to the [official Kubernetes blog here](https://kubernetes.io/blog/2018/07/18/11-ways-not-to-get-hacked/)