---
title: Cluster Autoscaler version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend to use a Cluster Autoscaler and Kubernetes version combination as per the guidance given by the official documentation:

| Kubernetes Version | Cluster Autoscalar Version |
| :----------------- | :------------------------- |
| `v1.27.X`          | `v1.27.X`                  |
| `v1.26.X`          | `v1.26.X`                  |
| `v1.25.X`          | `v1.25.X`                  |
| `v1.24.X`          | `v1.24.X`                  |
| `v1.23.X`          | `v1.23.X`                  |
| `v1.22.X`          | `v1.22.X`                  |
| `v1.21.X`          | `v1.21.X`                  |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of Cluster Autoscaler and Kubernetes will lead to unintended behavior and functionality may not work as expected. 

## Why does this exist? (Root Cause)

Starting from Kubernetes `1.12`, Cluster Autoscaler's versioning scheme was changed to match Kubernetes minor releases exactly.

## Additional Resources

For more details, please refer to the official [Cluster Autoscaler documentation](https://github.com/kubernetes/autoscaler/blob/master/cluster-autoscaler/README.md#releases).