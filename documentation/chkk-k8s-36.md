---
title: Image Pull Policy should not be set to Always
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Set ImagePullPolicy to `IfNotPresent` for each container.

```yaml sample-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: frontend
spec:
  containers:
  - name: app
    image: images.my-company.example/app:v4
+   imagePullPolicy: IfNotPresent
  - name: log-aggregator
    image: images.my-company.example/log-aggregator:v6
+   imagePullPolicy: IfNotPresent
```

## How to fix it, short-term workaround? (Mitigation)

Use the `IfNotPresent` image pull policy instead to minimize the impact of dependency (registry, network etc) failures.

## What is the impact? (Availability Impact)

If there's network disruption or the registry is down, your application launch will fail.

## Why does this exist? (Root Cause)

`imagePullPolicy=Always` means you're exercising your dependencies on every container launch. Upon every container launch, the image along with its dependencies will be pulled from the remote repository over the network. This makes the container launch process susceptible to network and remote 3rd party repository failures.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any Pod, Deployment, DaemonSet, StatefulSet, ReplicaSet, ReplicationController, Job or CronJob spec.

_Affected Images_  
All container images with `imagePullPolicy` set to `Always`

## Additional Resources

For more details on using images for containers, please refer to the official Kubernetes blog here: [K8s Configuration Best Practices](https://kubernetes.io/docs/concepts/configuration/overview/)