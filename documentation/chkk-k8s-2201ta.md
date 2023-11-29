---
title: Crossplane is not compatible with your current version of Kubernetes.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Depending on the Crossplane version that you're using, please upgrade your Kubernetes cluster accordingly.

| Crossplane Version | Kubernetes Version                                                                                                                                                                                                 |
| :----------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `v1.10`            | Upgrade your cluster to Kubernetes `v1.16` or greater.                                                                                                                                                             |
| `v1.11`, `v1.12`   | Upgrade your Kubernetes Cluster version to a version currently supported by the Kubernetes Community as mentioned within the [official Kubernetes documentation](https://kubernetes.io/releases/#release-history). |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Crossplane is not compatible with the version of Kubernetes your cluster is running. This means that your software is prone to incompatibilities and may lead to undefined behavior.

## Why does this exist? (Root Cause)

An actively supported Kubernetes version is a pre-requisite for installing Crossplane as mentioned within their documentation.

## Additional Resources

For more information please refer to the following

1. [Crossplane installation prerequisites for v1.12](https://docs.crossplane.io/latest/software/install/#prerequisites).
2. [Crossplane installation prerequisites for v1.11](https://docs.crossplane.io/v1.11/software/install/)
3. [Crossplane installation prerequisites for v1.10](https://docs.crossplane.io/v1.10/reference/install/)