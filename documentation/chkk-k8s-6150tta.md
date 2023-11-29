---
title: Incompatible version of Kubernetes with Vertical Pod Autoscaler
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term  fix? (Remediation)

Upgrade Vertical Pod Autoscaler to a version compatible with your Kubernetes version. Refer to the following compatibility matrix for more information:

| VPA version      | Kubernetes version |
| ---------------- | ------------------ |
| `v.1.0`          | `v1.25+`           |
| `v0.14`          | `v1.25+`           |
| `v0.13`          | `v1.25+`           |
| `v0.12`          | `v1.25+`           |
| `v0.11`          | `v1.22 - v1.24`    |
| `v0.10`          | `v1.22+`           |
| `v0.9`           | `v1.16+`           |
| `v0.8`           | `v1.13+`           |
| `v0.4 to v0.7`   | `v1.11+`           |
| `v0.3` and lower | `v1.7+`            |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running Vertical Pod Autoscaler on an incompatible version of Kubernetes will lead to an unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Vertical Pod Autoscaler maintains an official support matrix on their GitHub. Using a version of Kubernetes not supported by Vertical Pod Autoscaler introduces incompatibilities in your software and may lead to undefined behavior.

## Additional Resources

For more information, please refer to the Vertical Pod Autoscaler [official GitHub documentation](https://github.com/kubernetes/autoscaler/blob/master/vertical-pod-autoscaler/README.md#compatibility)