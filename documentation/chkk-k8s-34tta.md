---
title: PodSecurityPolicy should restrict assigning NET_RAW capability to Pods and Containers
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Disable NET_RAW capability for all Pods and Containers.

```yaml sample-pod-security-policy.yaml
---
apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: restricted
spec:
  allowPrivilegeEscalation: false
  allowedProcMountTypes:
    - Default
  hostIPC: false
  hostNetwork: false
  hostPID: false
  privileged: false # disallow privileged pods
+ requiredDropCapabilities: # Drop privileges in the Linux kernel
+    - NET_RAW
```

## What is the impact? (Availability Impact)

NET_RAW capability allows an unauthorized container process to act as an intercepting proxy for normal application layer communication.

## Affected Components

Containers and initContainers

## Additional Resources

For more details on configuring Pod Security Policies, please refer to the official Kubernetes documentation here: [K8S Pod Security Policies](https://kubernetes.io/docs/concepts/policy/pod-security-policy/)