---
title: Container Image Tag should not be latest or unset
category: 655c49ff76fdad0024723139
---

Severity: Medium

## How to fix it, long-term fix? (Remediation)

Define the container image tag/version that you expect to run instead of `latest`.

```yaml sample-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: frontend
spec:
  containers:
  - name: app
-   image: images.my-company.example/app
-   image: images.my-company.example/app:latest
+   image: images.my-company.example/app:v4
  - name: log-aggregator
-   image: images.my-company.example/log-aggregator
-   image: images.my-company.example/log-aggregator:latest
+   image: images.my-company.example/log-aggregator:v6
```

## How to fix it, short-term workaround? (Mitigation)

Specify container image tag. Do not use latest tag or leave it blank.

## What is the impact? (Availability Impact)

Pulling the latest image tag can introduce unexpected changes in your cluster which may impact the running cluster configuration causing traffic disruption across running applications.

## Why does this exist? (Root Cause)

Know what you're running in your production cluster. i.e. specify image tags. Not having tags means you're pulling latest on every image pull leading to unexpected behavior, potential application downtime, hard to debug failures and increased operational load.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any Pod, Deployment, DaemonSet, StatefulSet, ReplicaSet, ReplicationController, Job or CronJob spec.

_Affected Images_  
All container images with tag unset or set to `latest`

## Additional Resources

For more details on using image tags for containers, please refer to the official Kubernetes documentation here: [K8S Configuration Best Practices](https://kubernetes.io/docs/concepts/containers/images/#image-pull-policy)