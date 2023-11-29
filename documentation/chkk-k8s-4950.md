---
title: The detected version of Vector is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term  fix? (Remediation)

Upgrade your Kubernetes cluster to `v1.19` or greater.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of Vector and Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

According to the official documentation,

> Vector must be installed on Kubernetes `v1.15` or higher. Vector is tested with Kubernetes `v1.19` and higher.

## Additional Resources

For more information, please refer to the [Official Vector Documentation](https://vector.dev/docs/setup/installation/platforms/kubernetes/)