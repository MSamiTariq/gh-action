---
title: The detected metrics-server version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of metrics-server that is supported by your Kubernetes version as shown in the table below:

| Metrics Server Version | Kubernetes Version |
| :--------------------- | :----------------- |
| `v0.6.x`               | `1.19+`            |
| `v0.5.x`               | `1.8+`             |
| `v0.4.x`               | `1.8+`             |
| `v0.3.x`               | `v1.8 - v1.21`     |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of metrics-server and Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Kubernetes recommends using a metrics-server version that is supported by your control plane version. 

## Additional Resources

For more information scroll to the Installation of [Kubernetes Metrics Server documentation](https://kubernetes-sigs.github.io/metrics-server)