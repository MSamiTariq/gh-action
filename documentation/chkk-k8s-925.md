---
title: Nil Point Derence Causes KubeCosts' Overview Page to Crash
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Please upgrade your KubeCost version to `v1.101.2` or greater. 

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Due to this defect, users are unable to access the KubeCost dashboard which is essential for monitoring and managing Kubernetes costs.

## Why does this exist? (Root Cause)

The issue was caused by a nil point dereference error in one of the cost-model component’s files due to a result variable being set to nil.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using KubeCost version `v1.101.2` contain this Latent Availability Risk.

## Additional Resources

For more information, please refer to 

1. [Github Issue](https://github.com/kubecost/cost-analyzer-helm-chart/issues/2048)
2. [Release Notes for `v1.101.2`](https://github.com/kubecost/cost-analyzer-helm-chart/releases/tag/v1.101.2)