---
title: Restrict assigning additional capabilities to containers beyond the default set of ts fef
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Assign capabilities to containers within the default set. When _drop_ includes ALL, all of the root privileges are disabled for that container. some changes Availability Risk

```yaml sample-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: frontend
spec:
  containers:
    name: app
    image: images.my-company.example/app:v4
+   securityContext:
+     capabilities:
+        drop:
+         -ALL
```

## Why does this exist? (Root Cause)

In general, containers should not be assigned capabilities beyond the default set. This poses a high security risk as it provides containers with privileges that are traditionally associated with the superuser.

## Affected Components

Containers and initContainers

## Additional Resources

For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/)
