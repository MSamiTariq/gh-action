---
title: Container Memory requests should be set
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Set the Memory requests at `spec.containers[].resources.requests.memory` for each container and at `spec.initContainers[].resources.requests.memory` for each initContainer.

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
+     requests:
+       memory: "64Mi"
  containers:
  - name: app
    image: images.my-company.example/app:v4
    resources:
+     requests:
+       memory: "64Mi"
```

For more details on efficiently managing resources for containers, please refer to the official Kubernetes documentation here: [K8s-Managing-Resources-for-Containers](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/)

## How to fix it, short-term workaround? (Mitigation)

Set the Memory requests at `spec.containers[].resources.requests.memory` for each container and at `spec.initContainers[].resources.requests.memory` for each initContainer.

## What is the impact? (Availability Impact)

Not having Memory requests prevents the scheduler from making informed Memory allocation on nodes, often scheduling your applications on nodes with less than required Memory.

## Why does this exist? (Root Cause)

Memory requests define what the container is guaranteed to get. Memory requests ensure your application the guaranteed Memory allocation.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes versions.

_Affected Images_  
All Pods, Deployments, Daemonsets including containers and initContainers that do not have memory requests defined are affected by this.

## Additional Resources

For further details, please refer to the [official Kubernetes documentation.](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/)