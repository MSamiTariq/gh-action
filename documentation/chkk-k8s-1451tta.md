---
title: The detected Contour version is not compatible with your Kubernetes version
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Use a version of Contour that is supported for your version of Kubernetes. Please refer to the following table for compatible versions:

| Contour Version | Kubernetes Supported Versions |
| :-------------- | :---------------------------- |
| `v1.27.x`       | `v1.26 - v1.28`               |
| `v1.26.x`       | `v1.26 - v1.28`               |
| `v1.25.x`       | `v1.25 - v1.27`               |
| `v1.24.x`       | `v1.24 - v1.26`               |
| `v1.23.x`       | `v1.23 - v1.25`               |
| `v1.22.x`       | `v1.22 - v1.24`               |
| `v1.21.x`       | `v1.21 - v1.23`               |
| `v1.20.x`       | `v1.21 - v1.23`               |
| `v1.19.x`       | `v1.20 - v1.22`               |
| `v1.18.x`       | `v1.19 - v1.21`               |
| `v1.17.x`       | `v1.19 - v1.21`               |
| `v1.16.x`       | `v1.19 - v1.21`               |
| `v1.15.x`       | `v1.19 - v1.21`               |
| `v1.14.x`       | `v1.18 - v1.20`               |
| `v1.13.x`       | `v1.18 - v1.20`               |
| `v1.12.0`       | `v1.17 - v1.19`               |
| `v1.11.0`       | `v1.17 - v1.19`               |
| `v1.10.x`       | `v1.17 - v1.19`               |
| `v1.9.0`        | `v1.16 - v1.18`               |

Also, see Contour's [official upgrade guide](https://projectcontour.io/resources/upgrading/).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Running Contour on an incompatible version of Kubernetes may lead to unintended behavior and functionality may not work as expected.

## Why does this exist? (Root Cause)

Specific version combinations of Contour and Kubernetes are tested in CI, supported and recommended by the Contour maintainers. Refer to the Contour [official documentation](https://projectcontour.io/resources/compatibility-matrix/) for more information.

## Additional Resources

For more information see: [Contour compatibility matrix](https://projectcontour.io/resources/compatibility-matrix/)