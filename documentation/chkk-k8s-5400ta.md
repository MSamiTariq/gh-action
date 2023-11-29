---
title: The detected Rancher version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of Rancher that is supported for Kubernetes version. The tables below can be used as a reference for your cloud provider.

### EKS

| Rancher Version | Lowest Version Certified | Highest Version Certified |
| :-------------: | :----------------------: | :-----------------------: |
|     `v2.7.3`    |          `v1.23`         |   `v1.24.10-eks-48e63af`  |
|     `v2.7.2`    |          `v1.23`         |   `v1.24.10-eks-48e63af`  |
|     `v2.7.1`    |          `v1.23`         |   `v1.23.10-eks-15b7512`  |
|     `v2.7.0`    |          `v1.23`         |   `v1.23.10-eks-15b7512`  |
|    `v2.6.12`    |          `v1.20`         |   `v1.24.12-eks-ec5523e`  |

### AKS

| Rancher Version | Lowest Version Certified | Highest Version Certified |
| :-------------: | :----------------------: | :-----------------------: |
|     `v2.7.3`    |          `v1.23`         |         `v1.25.5`         |
|     `v2.7.2`    |          `v1.23`         |         `v1.25.5`         |
|     `v2.7.1`    |          `v1.23`         |         `v1.24.6`         |
|     `v2.7.0`    |          `v1.23`         |         `v1.24.6`         |
|    `v2.6.12`    |          `v1.20`         |         `v1.24.10`        |

### GKE

| Rancher Version | Lowest Version Certified | Highest Version Certified |
| :-------------: | :----------------------: | :-----------------------: |
|     `v2.7.3`    |          `v1.23`         |     `v1.25.6-gke.1000`    |
|     `v2.7.2`    |          `v1.23`         |     `v1.25.6-gke.1000`    |
|     `v2.7.1`    |          `v1.23`         |     `v1.24.5-gke.600`     |
|     `v2.7.0`    |          `v1.23`         |     `v1.24.5-gke.600`     |
|    `v2.6.12`    |          `v1.20`         |    `v1.24.12-gke.1000`    |

For other versions see the support map for your version on [Rancher's Docs](https://www.suse.com/suse-rancher/support-matrix/all-supported-versions).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running an incompatible version combination of Rancher and Kubernetes can lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Rancher recommends using a supported version of Kubernetes control plane.

## Additional Resources

For more information see: [Rancher-Kubernetes compatibility matrix](https://www.suse.com/suse-rancher/support-matrix/all-supported-versions)