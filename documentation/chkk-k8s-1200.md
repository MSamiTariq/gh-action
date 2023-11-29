---
title: Flux is running on an unsupported Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Flux requires Kubernetes cluster that matches one of the following versions 

| Kubernetes Version | Minimum Required |
| :----------------- | :--------------- |
| `v1.25`            | `>= v1.25.0`     |
| `v1.26`            | `>= v1.26.0`     |
| `v1.27`            | `>= v1.27.1`     |
| `v1.28` and later	 | `>= v1.28.0`     |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running Flux on an unsupported version of Kubernetes will lead to unintended behaviour and functionality may not work as expected.

## Why does this exist? (Root Cause)

Using a version of Kubernetes not supported by Flux introduces incompatibilities in your software and may lead to undefined behavior.

## Additional Resources

For more details, please refer to the [Flux Documentation](https://fluxcd.io/flux/installation/)