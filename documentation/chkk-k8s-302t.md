---
title: The detected cert-manager version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation))

Use a version of cert-manager that is supported for your version of Kubernetes. Check the table provided in the section below to see the supported versions.

Also see the [cert-manager upgrade guide](https://cert-manager.io/docs/installation/upgrading/).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of cert-manager and Kubernetes will lead to unintended behavior and functionality may not work as expected. 

## Why does this exist? (Root Cause)

cert-manager.io recommends using a Kubernetes control plane version for which it is supported. The supported version combinations are listed below:

| Release | Kubernetes versions |
| :------ | :------------------ |
| `v1.13` | `v1.23 → v1.28`     |
| `v1.12` | `v1.22 → v1.27`     |
| `v1.11` | `v1.21 → v1.27`     |
| `v1.10` | `v1.20 → v1.26`     |
| `v1.9`  | `v1.20 → v1.24`     |
| `v1.8`  | `v1.19 → v1.24`     |
| `v1.7`  | `v1.18 → v1.23`     |
| `v1.6`  | `v1.17 → v1.22`     |
| `v1.5`  | `v1.16 → v1.22`     |
| `v1.4`  | `v1.16 → v1.21`     |
| `v1.3`  | `v1.16 → v1.21`     |
| `v1.2`  | `v1.16 → v1.21`     |
| `v1.1`  | `v1.11 → v1.21`     |
| `v1.0`  | `v1.11 → v1.21`     |
| `v0.16` | `v1.11 → v1.21`     |
| `v0.15` | `v1.11 → v1.21`     |
| `v0.14` | `v1.11 → v1.21`     |
| `v0.13` | `v1.11 → v1.21`     |
| `v0.12` | `v1.11 → v1.21`     |
| `v0.11` | `v1.9 → 1v.21`      |

## Additional Resources

For more information see: [cert-manager supported releases](https://cert-manager.io/docs/installation/supported-releases/)