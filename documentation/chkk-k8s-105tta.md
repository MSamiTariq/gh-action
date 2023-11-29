---
title: Incompatible version of Istio with Kubernetes
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend to use an Istio and Kubernetes version combination as per the guidance given by the official documentation:

| Istio Version      | Supported Kubernetes Versions       |
| :----------------- | :---------------------------------- |
| `v1.20`            | `v1.25, v1.26, v1.27, v1.28`        |
| `v1.19`            | `v1.25, v1.26, v1.27, v1.28`        |
| `v1.18`            | `v1.24, v1.25, v1.26, v1.27`        |
| `v1.17`            | `v1.23, v1.24, v1.25, v1.26`        |
| `v1.16`            | `v1.22, v1.23, v1.24, v1.25`        |
| `v1.15`            | `v1.22, v1.23, v1.24, v1.25`        |
| `v1.14`            | `v1.21, v1.22, v1.23, v1.24`        |
| `v1.13`            | `v1.20, v1.21, v1.22, v1.23`        |
| `v1.12`            | `v1.19, v1.20, v1.21, v1.22`        |
| `v1.11`            | `v1.18, v1.19, v1.20, v1.21, v1.22` |
| `v1.10`            | `v1.18, v1.19, v1.20, v1.21`        |
| `v1.9`             | `v1.17, v1.18, v1.19, v1.20`        |
| `v1.8`             | `v1.16, v1.17, v1.18, v1.19`        |
| `v1.7`             | `v1.16, v1.17, v1.18`               |
| `v1.6` and earlier |                                     |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of Istio and Kubernetes will lead to unintended behavior and functionality may not work as expected. 

## Why does this exist? (Root Cause)

Istio recommends using the version combinations for Istio and Kubernetes specified within the aforementioned table.

## Additional Resources

For more details, please refer to the official [Istio Releases documentation](https://istio.io/latest/docs/releases/supported-releases/#support-status-of-istio-releases)