---
title: Specific KEDA Operator versions are prone to crash depending on Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade KEDA to `v2.9.3` or later if you have k8s `>= v1.23`, otherwise, use KEDA `v2.8.2`. You can upgrade KEDA to the latest version using the following command if you installed using Helm:

```shell Upgrade to latest version
helm upgrade keda kedacore/keda
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

KEDA operator being in CrashLoopBackoff can impact autoscaling, resource utilization, monitoring, and troubleshooting resulting in potential outages and/or increase in infrastructure cost.

## Why does this exist? (Root Cause)

This defect occurs because an object is passed to the KEDA scaler's cache without being deep copied. This causes a nil pointer dereference when the object is accessed.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
KEDA `< v2.9.3` for Kubernetes `>= v1.23`  
KEDA `!= 2.8.2` for Kubernetes `<1.23`

_Affected Images_  
All VPC CNI images

## Additional Resources

For more details, please refer to the following:

- [GitHub Issue](https://github.com/kedacore/keda/issues/4207)
- [GitHub Issue](https://github.com/kedacore/keda/issues/4270)