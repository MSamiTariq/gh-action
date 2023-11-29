---
title: Kube-State-Metrics might panic if the pod status container statuses do not match the containers in spec
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your kube-state-metrics version to `v2.5.0` or greater.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

This defect might cause kube-state-metrics to panic, crash, and not function properly. This could result in a loss of metrics and monitoring data for the cluster.

## Why does this exist? (Root Cause)

This defect occurs if the container statuses in a pod's status do not match the containers in spec.

The exact reason as to why it happens is currently unclear and Chkk is communicating with the kube-state-metrics community to understand the root-cause. Once we do, this KBA will be updated accordingly.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using kube-state-metrics versions `>= v2.3.0` and `< v2.5.0` contain this Latent Availability Risk.

## Additional Resources

For more information, please refer to the following:

1. [PR that fixed this issue](https://github.com/kubernetes/kube-state-metrics/pull/1723)

2. [PR that resolved another related issue](https://github.com/kubernetes/kube-state-metrics/pull/1731)