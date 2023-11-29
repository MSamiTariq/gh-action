---
title: The detected Cortex version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your kubernetes control plane version to at least `v1.22`

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an incompatible version combination of Cortex and Kubernetes can lead to unintended behaviour and functionality may not work as expected.

## Why does this exist? (Root Cause)

Cortex recommends using a supported version of kubernetes control plane. The minimum supported version of kubernetes for Cortex is `v1.22`.

## Additional Resources

For more information, please refer to: [Cortex Baseline System Configuration](https://cognitivescale.github.io/cortex-charts/docs/cluster-sizing/#baseline-system-configuration)