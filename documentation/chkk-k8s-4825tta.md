---
title: Your Cluster’s Kubernetes version is not compatible with the detected version of Nacos
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your Kubernetes cluster to `v1.12.2` or greater.

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of Nacos and Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Nacos recommends installing it on a supported version of Kubernetes. The minimum supported version of Kubernetes for Nacos is `v1.12.2`.

## Additional Resources

For more information, please refer to the [Official Nacos Documentation](https://nacos.io/en-us/docs/use-nacos-with-kubernetes.html#:~:text=Kubernetes%20version%EF%BC%9A1.12.2%2B)