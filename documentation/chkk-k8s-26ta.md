---
title: Define security context for Pods and Containers
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Define explicit security context either at Pod or Container level, or both.

```yaml sample-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: security-context-demo
spec:
+ securityContext:
+   runAsUser: 1000
+   runAsGroup: 3000
+   fsGroup: 2000
  volumes:
  - name: sec-ctx-vol
    emptyDir: {}
  containers:
  - name: SampleSecContext
    image: busybox
    command: [ "sh", "-c", "sleep 1h" ]
    volumeMounts:
    - name: sec-ctx-vol
      mountPath: /data/demo
+   securityContext:
+     allowPrivilegeEscalation: false
```

## Why does this exist? (Root Cause)

Undefined security context can lead to unauthorized, unrestricted and insecure activity of container processes.

## Affected Components

Containers and initContainers

## Additional Resources

For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/)