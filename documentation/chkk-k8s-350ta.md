---
title: The detected containerd version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of containerd that is supported for Kubernetes version. The table below can be used as a reference.

| Kubernetes Version | Containerd Version    |
| :----------------- | :-------------------- |
| `v1.24`            | `v1.7.0+`, `v1.6.4+`  |
| `v1.25`            | `v1.7.0+`, `v1.6.4+`  |
| `v1.26`            | `v1.7.0+`, `v1.6.15+` |
| `v1.27`            | `v1.7.0+`, `v1.6.15+` |
| `v1.28`            | `v1.7.0+`, `v1.6.15+` |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of containerd and Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

containerd recommends using a supported version of Kubernetes control plane.

## Additional Resources

For more information see: [containerd-Kubernetes compatibility matrix](https://containerd.io/releases/#kubernetes-support)