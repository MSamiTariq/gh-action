---
title: Do not allow NET_RAW capability on Containers
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Disable NET_RAW capability for all Pods and Containers.

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
+       drop:
+        - NET_RAW
```

## What is the impact? (Availability Impact)

NET_RAW capability allows an unauthorized container process to act as an intercepting proxy for normal application layer communication.

## Affected Components

Containers and initContainers

## Additional Resources

For more details on configuring Pod Security Policies, please refer to the official Kubernetes documentation here: [K8S Pod Security Policies](https://kubernetes.io/docs/concepts/policy/pod-security-policy/)