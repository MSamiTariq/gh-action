---
title: Incompatible version of Kubernetes with Datadog Operator
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your Kubernetes cluster to `1.20.0` or greater.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running Datadog Operator on an incompatible version of Kubernetes will lead to an unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

The detected Datadog Operator version is not compatible with your Kubernetes version. [According to the official Datadog documentation](https://docs.datadoghq.com/containers/kubernetes/installation/?tab=operator#prerequisites):  
_Tests were done on versions `>= 1.20.0`. Still, it should work on versions `>= v1.11.0`. For earlier versions, because of limited CRD support, the Operator may not work as expected._

## Additional Resources

For more information, please refer to the [Official Datadog Documentation](https://docs.datadoghq.com/containers/kubernetes/installation/?tab=operator#prerequisites)