---
title: Incompatible version of Kubernetes Control Plane with Kong Kubernetes Ingress Controller
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend to use a Kubernetes Control Plane and Kong Kubernetes Ingress Controller version combination as per the guidance given by the official documentation:

| Kubernetes Version | Compatible Kubernetes Ingress Controller Versions    |
| :----------------- | :--------------------------------------------------- |
| `v1.16`            | `None`                                               |
| `v1.17`            | `None`                                               |
| `v1.18`            | `None`                                               |
| `v1.19`            | `None`                                               |
| `v1.20`            | `None`                                               |
| `v1.21`            | `None`                                               |
| `v1.22`            | `2.6.X, 2.7.X, 2.8.X, 2.9.X, 2.10.X, 2.11.X`         |
| `v1.23`            | `2.6.X, 2.7.X, 2.8.X, 2.9.X, 2.10.X, 2.11.X, 2.12.X` |
| `v1.24`            | `2.6.X, 2.7.X, 2.8.X, 2.9.X, 2.10.X, 2.11.X, 2.12.X` |
| `v1.25`            | `2.6.X, 2.7.X, 2.8.X, 2.9.X, 2.10.X, 2.11.X, 2.12.X` |
| `v1.26`            | `2.6.X, 2.7.X, 2.8.X, 2.9.X, 2.10.X, 2.11.X, 2.12.X` |
| `v1.27`            | `2.6.X, 2.7.X, 2.8.X, 2.9.X, 2.10.X, 2.11.X, 2.12.X` |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an unsupported version combination of Kubernetes Control Plane and Kong Kubernetes Ingress Controller will lead to an unintended behavior and functionality may not work as expected. 

## Why does this exist? (Root Cause)

Kong documentation recommends using the compatible version combinations of Kubernetes Control Plane and Kong Kubernetes Control Plane.

## Additional Resources

For more details, please refer to the [official Kong documentation ](https://docs.konghq.com/kubernetes-ingress-controller/2.7.x/references/version-compatibility/#kubernetes)