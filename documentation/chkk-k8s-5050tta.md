---
title: Incompatible version of Kubernetes with MetalLB
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your Kubernetes cluster to `v1.13.0` or greater.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running MetalLB on an incompatible version of Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

It is recommended to run MetalLB on one of the supported Kubernetes releases. According to MetalLB's official documentation: 

_It requires a Kubernetes cluster, running Kubernetes `v1.13.0` or later_

## Additional Resources

For more information, please refer to the [Official MetalLB Documentation](https://metallb.universe.tf/#requirements)