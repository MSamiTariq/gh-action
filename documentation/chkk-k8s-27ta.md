---
title: Container CPU limits should be set
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Set the CPU limits at `spec.containers[].resources.limits.cpu` for each container and at `spec.initContainers[].resources.limits.cpu` for each initContainer when scheduling a Pod. The following sample Pod manifest shows CPU limits assigned for individual containers and initContainers.

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
+       cpu: "500m" # Set CPU limit
  containers:
  - name: app
    image: images.my-company.example/app:v4
    resources:
+     limits:  # Define resource limits for container
+       cpu: "500m" # Set CPU limit
```

## How to fix it, short-term workaround? (Mitigation)

1. Set the CPU limits at `spec.containers[].resources.limits.cpu` for each container.
2. Set the CPU limits at `spec.initContainers[].resources.limits.cpu` for each initContainer.

## What is the impact? (Availability Impact)

Problematic containers can take up more CPU than they should causing a node wide impact and bringing down all the applications on the node.

## Why does this exist? (Root Cause)

Containers CPU limits should be bounded and carefully set. CPU limit is a guard rail to protect against bad code and reduce the blast radius to the impacted application only.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes versions.

_Affected Images_  
All Pods, Deployments, Daemonsets including containers and initContainers are affected by this.

## Additional Resources

For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/)