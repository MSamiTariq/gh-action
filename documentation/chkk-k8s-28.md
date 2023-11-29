---
title: Container CPU requests should be set
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Set the CPU requests at `spec.containers[].resources.requests.cpu` for each container and at `spec.initContainers[].resources.requests.cpu` for each initContainer. 

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
+     requests:  # Define resource limits for init container
+       cpu: "250m"
  containers:
  - name: app
    image: images.my-company.example/app:v4
    resources:
+     requests:
+       cpu: "250m"
```

## How to fix it, short-term workaround? (Mitigation)

 Set the CPU requests at `spec.containers[].resources.requests.cpu` for each container and at `spec.initContainers[].resources.requests.cpu` for each initContainer.

## What is the impact? (Availability Impact)

Not having CPU requests prevents the scheduler from making informed CPU allocation on nodes, often scheduling your applications on nodes with less than required CPU.

## Why does this exist? (Root Cause)

CPU requests define what the container is guaranteed to get. CPU requests ensures your application the guaranteed CPU allocation.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes versions.

_Affected Images_  
All Pods, Deployments, Daemonsets including containers and initContainers are affected by this.

## Additional Resources

For more details, please refer to the official [Kubernetes Documentation](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/).