---
title: Incompatible version of Kong Kubernetes Ingress Controller with Open Source Kong Gateway
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend to use a Kong Open Source Gateway and Kubernetes Ingress Controller version combination as per the guidance given by the official documentation:

| Kong Open Source Gateway Version | Compatible Kubernetes Ingress Controller Versions                    |
| :------------------------------- | :------------------------------------------------------------------- |
| `v2.0`                           | `v2.1, v2.2, v2.3, v2.4, v2.5, v2.6, v2.7, v2.8, v2.9, v2.10, v2.11` |
| `v2.1`                           | `v2.1, v2.2, v2.3, v2.4, v2.5, v2.6, v2.7, v2.8, v2.9, v2.10, v2.11` |
| `v2.2`                           | `v2.1, v2.2, v2.3, v2.4, v2.5, v2.6, v2.7, v2.8, v2.9, v2.10, v2.11` |
| `v2.3`                           | `v2.1, v2.2, v2.3, v2.4, v2.5, v2.6, v2.7, v2.8, v2.9, v2.10, v2.11` |
| `v2.4`                           | `v2.1, v2.2, v2.3, v2.4, v2.5, v2.6, v2.7, v2.8, v2.9, v2.10, v2.11` |
| `v2.5`                           | `v2.1, v2.2, v2.3, v2.4, v2.5, v2.6, v2.7, v2.8, v2.9, v2.10, v2.11` |
| `v2.6`                           | `v2.1, v2.2, v2.3, v2.4, v2.5, v2.6, v2.7, v2.8, v2.9, v2.10, v2.11` |
| `v2.7`                           | `v2.1, v2.2, v2.3, v2.4, v2.5, v2.6, v2.7, v2.8, v2.9, v2.10, v2.11` |
| `v2.8`                           | `v2.1, v2.2, v2.3, v2.4, v2.5, v2.6, v2.7, v2.8, v2.9, v2.10, v2.11` |
| `v3.0`                           | `v2.7, v2.8, v2.9, v2.10, v2.11`                                     |
| `v3.1`                           | `v2.7, v2.8, v2.9, v2.10, v2.11`                                     |
| `v3.2`                           | `v2.7, v2.8, v2.9, v2.10, v2.11`                                     |
| `v3.3`                           | `v2.7, v2.8, v2.9, v2.10, v2.11`                                     |
| `v3.4`                           | `v2.7, v2.8, v2.9, v2.10, v2.11`                                     |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of Kong Kubernetes Ingress Controller and Kong Gateway will lead to an unintended behavior and functionality may not work as expected. 

## Why does this exist? (Root Cause)

Kong documentation recommends using the version of Kong Open Source Gateway with the Kong Kubernetes Ingress Controller version for which it was meant.

## Additional Resources

For more details, please refer to the [official Kong documentation ](https://docs.konghq.com/kubernetes-ingress-controller/2.7.x/references/version-compatibility/#kong)