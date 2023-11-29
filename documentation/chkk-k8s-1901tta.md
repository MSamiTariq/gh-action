---
title: Cluster Autoscaler may face Segmentation Faults.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade cluster-autoscaler to `v1.21.3` or later.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Cluster Autoscaler versions `<1.21.3` may face Segmentation Faults due to null pointer dereference crashing the Cluster Autoscaler Pods. This can lead to your cluster not being able to scale.

## Why does this exist? (Root Cause)

Cluster Autoscaler provisioned on a cluster running on EKS, GKE or AKS checks for the NodeGroup associated with any Node while performing several operations. The NodeGroup check may return a nil value and a bug in Cluster Autoscaler versions `<1.21.3` may result in a Segmentation Fault/have been reported to have caused Segmentation Faults.

## Who is impacted and when? (Trigger Conditions)

Cluster Autoscaler versions `<1.21.3` will have this risk.

## Additional Resources

Details of the exact GitHub issue can be found [here](https://github.com/kubernetes/autoscaler/issues/4741)