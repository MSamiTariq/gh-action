---
title: Multiple pod replicas should be configured for High Availability
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use multiple pod replicas of your application to ensure high availability and fault tolerance.

```yaml k8s manifest
# The example given below shows how to set replica in manifest file for deployment

kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 2
```
```yaml kubectl
# The example given below shows how to increase pod replicas of deployment

kubectl scale deployment/<deployment-name> --replicas=2
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

## How to fix it, short-term workaround? (Mitigation)

Scale the pod replicas in your Deployment/ReplicaSet/ReplicationController/StatefulSet to > 1

## What is the impact? (Availability Impact)

Using a single replica pod can result in a single point of failure for your application, causing intermittent and sometimes even prolonged traffic disruption.

## Why does this exist? (Root Cause)

Running multiple replicas Pods of an app helps it run in a highly-available manner. If one replica fails, the remaining replicas will still function.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes versions

_Affected Images_  
All images

## Additional Resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/)