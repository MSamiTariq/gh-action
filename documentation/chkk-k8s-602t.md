---
title: Pod replicas should be scheduled across nodes
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Schedule multiple pod replicas of your application across different nodes in different AZs to ensure high availability and fault tolerance.

## How to fix it, short-term workaround? (Mitigation)

Use pod [anti-affinity](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/) to spread replicas across multiple worker nodes.  
Use [pod topology spread constraints](https://kubernetes.io/docs/concepts/workloads/pods/pod-topology-spread-constraints/) to spread pods across AZs automatically.

## What is the impact? (Availability Impact)

Having all pod replicas for your application on the same node can make it susceptible to node failures, impacting the application availability.

## Why does this exist? (Root Cause)

Running multiple pod replicas across different nodes and Availability Zones (AZ) makes your application more resilient to node failures. If one replica fails in one region, the remaining replicas will still function.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All Kubernetes versions

_Affected Images_  
All images

## Additional Recources

For more details, please refer to the [official Kubernetes documentation ](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/)