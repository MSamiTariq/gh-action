---
title: Your Cluster’s Kubernetes version is not compatible with the detected version of OpenCost
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your Kubernetes cluster to `v1.20` or greater.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an incompatible version combination of OpenCost and Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

OpenCost recommends installing it on a supported version of Kubernetes. The minimum supported version of Kubernetes for OpenCost is `v1.20`.

## Additional Resources

For more information, please refer to the [Official OpenCost Documentation](https://github.com/opencost/opencost#getting-started)