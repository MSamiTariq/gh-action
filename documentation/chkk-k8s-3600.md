---
title: The detected Elastic Cloud on Kubernetes (ECK) Controller version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of the Elastic Cloud on Kubernetes (ECK) Controller that is supported for your version of Kubernetes. The table below can be used as reference:

| ECK Version | Supported Kubernetes Versions |
| :---------- | :---------------------------- |
| `v1.0.x`    | `v1.11 - v1.21`               |
| `v1.1.x`    | `v1.11 - v1.21`               |
| `v1.2.x`    | `v1.11 - v1.21`               |
| `v1.3.x`    | `v1.11 - v1.21`               |
| `v1.4.x`    | `v1.11 - v1.21`               |
| `v1.5.x`    | `v1.11 - v1.21`               |
| `v1.6.x`    | `v1.16 - v1.21`               |
| `v1.7.x`    | `v1.17 - v1.22`               |
| `v1.8.x`    | `v1.18 - v1.22`               |
| `v1.9.x`    | `v1.18 - v1.22`               |
| `v2.0.x`    | `v1.19 - v1.23`               |
| `v2.1.x`    | `v1.19 - v1.23`               |
| `v2.2.x`    | `v1.19 - v1.23`               |
| `v2.3.x`    | `v1.20 - v1.24`               |
| `v2.4.x`    | `v1.20 - v1.24`               |
| `v2.5.x`    | `v1.21 - v1.25`               |
| `v2.6.x`    | `v1.21 - v1.25`               |
| `v2.7.x`    | `v1.22 - v1.26`               |
| `v2.8.x`    | `v1.24 - v1.27`               |
| `v2.9.x`    | `v1.24 - v1.28`               |
| `v2.10.x`   | `v1.24 - v1.28`               |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of the Elastic Cloud on Kubernetes (ECK) Controller and Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Elastic recommend using a Kubernetes control plane version for which the Elastic Cloud on Kubernetes (ECK) Controller is supported.

## Additional Resources

For more details, please refer to the official [Elastic documentation](https://www.elastic.co/support/matrix#matrix_kubernetes)