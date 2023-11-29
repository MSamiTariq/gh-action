---
title: Avoid running singleton Pods in the cluster
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use [Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) or [ReplicaSets](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) to deploy your application instead of using individual pods.

## How to fix it, short-term workaround? (Mitigation)

Re-deploy your application with Deployments or ReplicaSets.

## What is the impact? (Availability Impact)

If your entire application runs in a single Pod, then your application will be unavailable if that Pod gets terminated.

## Why does this exist? (Root Cause)

If a pod that is created by a Deployment fails or gets terminated, the Deployment controller will start a new pod to ensure the specified number of replica Pods are always running.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes clusters using any Pod spec.

_Affected Images_  
All images that directly provision a Pod spec.

## Additional Resources

For more details, please refer to the [official Kubernetes documentation](https://kubernetes.io/docs/concepts/configuration/overview/#naked-pods-vs-replicasets-deployments-and-jobs)