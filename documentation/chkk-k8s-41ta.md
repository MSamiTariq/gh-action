---
title: Container Memory limits should be set
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

The following sample Pod manifest shows Memory limits assigned for individual containers and initContainers.

```yaml sample-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: frontend
spec:
  initContainers:
  - name: init-cont
    image: initcont:v1.0
    resources:
+     limits:  # Define resource limits for init container
+       memory: "128Mi" # Set memory limit
  containers:
  - name: app
    image: images.my-company.example/app:v4
    resources:
+     limits:  # Define resource limits for container
+       memory: "128Mi" # Set memory limit
```

## How to fix it, short-term workaround? (Mitigation)

Set the Memory limits at `spec.containers[].resources.limits.memory` for each container and at `spec.initContainers[].resources.limits.memory` for each initContainer when scheduling a Pod.

## What is the impact? (Availability Impact)

Problematic containers can take up more Memory than they should causing a node wide impact and bringing down all the applications on the node.

## Why does this exist? (Root Cause)

Container Memory limits should be set. Memory limit is a guard rail to protect against bad code and reduce the blast radius to the impacted application only.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes versions.

_Affected Images_  
All Pods, Deployments, Daemonsets including containers and initContainers are affected by this.

## Additional Resources

For more details on efficiently managing resources for containers, please refer to the official Kubernetes documentation here: [K8S Manage Resources for Containers](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/)